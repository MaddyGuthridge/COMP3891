Contains processor control registers, which manage exceptions and interrupts.

Can only be accessed using `mtc0` (move to coprocessor 0) and `mfc0` (move from coprocessor 0) instructions. These instructions require the kernel [[execution mode]].

## Registers

### `c0_cause`
Cause of the recent exception (interrupt)

### `c0_status`
Current status of the CPU. Has a bunch of flag bits to contain a bunch of information to control the processor.

Here are some of them (but not all of them for the sake of space)
| name  | bit | purpose                                            | values                |
| ----- | --- | -------------------------------------------------- | --------------------- |
| `IEc` | 0   | Controls whether interrupts are enabled            | 0=disabled, 1=enabled |
| `KUc` | 1   | Controls whether we're in kernel mode or user mode | 0=kernel, 1=user      |
| `KUp` |     |                                                    |                       |

### `c0_epc`
exception program counter: address of instruction that caused the [[exception]].

### `c0_badvaddr`
Address accessed that caused the exception (eg for segfaults and the like)