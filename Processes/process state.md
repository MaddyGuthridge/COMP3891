Represents the state of a [[process]] or [[thread]]. This is used to help manage [[context switch|context switches]].

## Running
- Currently on CPU
- Processes can voluntarily `Yield()` their CPU time to other processes if they need to wait for things to happen

## Blocked
Waiting for some operation to complete (eg I/O)

## Ready
Ready to run, but not currently running

## Zombie
The process is dead, but the [[kernel]] hasn't quite gotten around to burying it yet.

Yikes? Well, [not really](https://unix.stackexchange.com/a/106004/161355).
