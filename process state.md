Represents the state of a [[process]] or [[thread]]. This is used to help manage [[context switching]]

## Running
- Currently on CPU
- Processes can voluntarily `Yield()` their CPU time to other processes if they need to wait for things to happen

## Blocked
- Waiting for some operation to complete (eg I/O)

## Ready
- Ready to run, but not currently running