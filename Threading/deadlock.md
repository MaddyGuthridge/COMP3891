Causes for deadlock
- Mutual exclusion (resources can't be accessed concurrently)
- Hold and wait (task is holding resources while waiting for other resources)
- No preemption
- Circular wait (each task depends on another task)

Solutions for deadlock
- Make resources not mutually exclusive
- Make threads only use one resource at once
- Take