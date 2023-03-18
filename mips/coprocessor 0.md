Contains processor control registers, which manage exceptions and interrupts.

Can only be accessed using `mtc0` (move to coprocessor 0) and `mfc0` (move from coprocessor 0) instructions. These instructions require the kernel [[execution mode]].

## Registers

### `c0_cause`
Cause of the recent exception (interrupt).

We mainly care about `ExcCode` in bits 2-6 (inclusive). This contains the code number for the exception type.

### `c0_status`
Current status of the CPU. Has a bunch of flag bits to contain a bunch of information to control the processor.

Here are some of them (but not all of them for the sake of space)
| name  | bit | purpose                                            | values                |
| ----- | --- | -------------------------------------------------- | --------------------- |
| `IEc` | 0   | Controls whether interrupts are enabled            | 0=disabled, 1=enabled |
| `KUc` | 1   | Controls whether we're in kernel mode or user mode | 0=kernel, 1=user      |
| `KUp` | 2   | Previous value for whether interrupts were enabled |                       |
| `IEp` | 3   | Previous value for kernel/user mode                |                       |
| `KUo` | 4   | Previous previous (old) value for interrupts enabled     |                       |
| `IEo` | 5   | Previous previous (old) value for kernel/user mode       |                       |

Note that is an exception is given within an exception, the bits are shifted, so current values become previous values, and previous values become old values.

### `c0_epc`
exception program counter: address of instruction that caused the [[exception]].

This is where the [[kernel]] should return to after handling the exception, after doing any necessary tidy-up.

### `c0_badvaddr`
Address accessed that caused the exception (eg for segfaults and the like)
