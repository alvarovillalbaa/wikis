# .delay() vs .apply_async() for Celery

In Celery, `.delay()` and `.apply_async()` both enqueue a task for asynchronous execution, but they offer different levels of control:

---

### `.delay(*args, **kwargs)`

- **Sugar for the common case.**
- Internally calls `.apply_async(args=args, kwargs=kwargs)` with *no extra options*.
- You can only pass the positional and keyword arguments that your task function accepts.
- **Use when** you just want “fire-and-forget” with default routing, no ETA/countdown, and no special options.

```python
# simple: pass x and y, use default queue, immediate execution
result = my_task.delay(3, 5)

```

---

### `.apply_async(args=None, kwargs=None, **options)`

- **Full power API.**
- You pass a tuple `args` and/or dict `kwargs` just like `.delay()`, **plus** any of Celery’s delivery options:
    - `queue="high_priority"`
    - `countdown=60` (seconds from now)
    - `eta=datetime(...)` (run at exact time)
    - `expires=3600` or `datetime(...)` (message TTL)
    - `priority=5`
    - `retry`, `serializer`, `headers`, `task_id`, `link`, `link_error`, etc.
- **Use when** you need to schedule for later, route to a specific queue, set a unique task ID, chain callbacks, or tweak any other broker/task parameters.

```python
from datetime import datetime, timedelta

# run in 10 minutes on the "reports" queue, priority 3
result = generate_report.apply_async(
    args=[user_id],
    kwargs={'detailed': True},
    countdown=600,
    queue='reports',
    priority=3,
)

# run at a precise ETA
eta = datetime.utcnow() + timedelta(hours=1)
result = send_reminder.apply_async(
    args=[task_id],
    eta=eta,
    expires=eta + timedelta(minutes=30),
)

```

---

### TL;DR

- **Use `.delay()`** for quick, immediate, default-option task calls.
- **Use `.apply_async()`** whenever you need to customize *when*, *where*, or *how* Celery delivers the task.