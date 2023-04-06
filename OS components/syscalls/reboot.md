A [[syscall]] to control the power of the system.

```c
int reboot(int code);
```

## Codes

- `RB_REBOOT` - the system is rebooted
- `RB_HALT` - the system is halted (basically an endless empty for loop on each CPU)
- `RB_POWEROFF` - the system is shut down
