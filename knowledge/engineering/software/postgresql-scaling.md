# PostgreSQL Scaling

OpenAI's 2026 PostgreSQL case study is durable evidence that single-primary PostgreSQL can support very large read-heavy products when the system deliberately offloads writes, constrains schema change risk, and applies layered load shedding.

## Compiled Truth
- Single-primary PostgreSQL can serve very high read-heavy traffic when writes remain bounded, replicas carry geographic read load, and the application treats the primary as a scarce write coordination point.
- OpenAI's reported shape: one Azure PostgreSQL primary plus nearly 50 read replicas, millions of QPS, low double-digit millisecond p99 client-side latency, five-nines availability, and one SEV-0 PostgreSQL incident over the prior 12 months.
- MVCC is the write-side constraint: updates copy rows, create dead tuples, amplify reads/writes, bloat tables/indexes, and make autovacuum tuning operationally important.
- Common overload chain: cache miss surge, expensive joins, or write storm raises database latency; client timeouts trigger retries; retries amplify load and can degrade broad product surfaces.
- Write strategy: move shardable write-heavy workloads to sharded systems, avoid unnecessary writes, rate-limit backfills, and default new write-heavy features away from the legacy single-primary deployment.
- Schema strategy: allow only lightweight operations, use strict timeouts, create/drop indexes concurrently, and avoid full table rewrites. Long-running backfills are acceptable if rate limits preserve production stability.
- Read strategy: place replicas close to users for latency, but account for WAL fanout. Cascading replication can scale replica count by letting intermediate replicas relay WAL, but it adds failover complexity.
- Load-shedding strategy: rate-limit at application, pooler, proxy, and query layers; prevent retry storms; block expensive query digests when needed. Query-level controls are the escape hatch for localized pathological load.
- Inference: PostgreSQL remains viable at surprising scale when the workload is read-heavy and the team is willing to push writes, sharding, cache policy, retries, schema change, and query shape into explicit operating rules.

## Implications
- For engineering: do not shard PostgreSQL by reflex. First classify read/write shape, isolate write-heavy paths, and harden retry, rate-limit, and schema-change controls.
- For agents: database-scaling recommendations should ask for workload mix, write amplification, retry behavior, replica topology, schema-change process, and backfill policy before prescribing a distributed database.
- For future work: compare this case against systems that truly require multi-writer distributed databases; the boundary is write pressure and operational complexity, not table count alone.

## Open Threads
- Which Clous services have write-heavy paths that should bypass the main relational database early?
- What query-digest or ORM-level rate-limit hooks exist in the current stack?

## Sources
- https://openai.com/index/scaling-postgresql/ — accessed 2026-05-21
- `raw/UNPROCESSED.md` — residual URL previously marked blocked.

## Change Log
- 2026-05-21 — Created from readable residual OpenAI PostgreSQL scaling source.
