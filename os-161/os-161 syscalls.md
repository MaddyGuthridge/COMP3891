The following conventions are used for [[syscall|syscalls]] on [[os-161]].

- Normal C function calling convention

## On call
- Register `v0` contains the syscall number

## On return
- Register `a3` contains `0` if the syscall was a success
- `v0` contains the result if success, otherwise the [[errno]] if a failure.