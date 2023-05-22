## User mode
Only limited registers and instructions allowed. Attempts to perform illegal operations give an exception to the [[kernel]]. Privileged operations should be done using [[syscall]]s.

## Kernel mode (aka privileged mode)
All instructions allowed, and process can access all registers. Access only given to the [[kernel]]