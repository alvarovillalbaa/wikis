# Kubernetes As Feedback Controllers

Kubernetes is a framework for closed feedback loops plus a consistent store for setpoints and a shared event bus. Operators reconcile desired vs observed state; they are thermostats, not one-shot scripts.

## Compiled Truth
- Open-loop (`ssh` + hope) assumes the action worked. Closed-loop repeatedly measures and acts until reality matches intent. Actions must be idempotent.
- Control-theory map: `.spec` = setpoint (never write your own spec from inside the controller); `.status` = measured variable; error = spec−status; controller = reconcile body; actuator = API writes; plant = the workload (Postgres, disk, Pod).
- Edge-triggered notifications, level-triggered logic: watch events only say *when* to look; Reconcile gets a namespace/name key and reads current state. Missed/duplicated events do not permanently desync the world. Delta-apply on edges overshoots (1→3 replica event applied twice → 5).
- Informer cache: cheap local reads, writes go to the API server; cache is eventually consistent. Read-after-write can double-create children. Fixes: expectations pattern (ReplicaSet) or `apiReader` for the dangerous list. Coalesce, rate-limit, worker pool on the work queue.
- `observedGeneration < generation` means status does not yet reflect latest intent.
- Cascade control: outer loop writes inner objects' specs (PVC, Pod); kubelet/scheduler/CSI/CNI are independent loops chained by the API server and ownerReferences. Node death → Pod delete edge → parent reconcile → new Pod → scheduler → kubelet.
- Observe is a snapshot gathered once at the top (kube objects + live DB health + effective config + slow collector metrics). Partial sensor failure is a measured fact, not an abort. Status writes last.
- Not every edge is the API server: disk-usage collectors should fire on threshold *crossings*, plus a resyncer safety net. Leader election prevents dual writers. Sampling interval should match how fast the plant changes.
- Declarative model leaks on imperative stateful ops (failover, major upgrade, migration): those need idempotent encoding of in-flight work. Operators move complexity into code; they do not remove it.

## Evidence
- 2026-08-13 | Fatih Arslan / PlanetScale: walkthrough from hand-run Postgres to controller-runtime, including production operator observation fan-in.

## Sources
- https://planetscale.com/blog/the-feedback-loops-behind-kubernetes
