A semaphore is a synchronisation primitive for preventing [[race condition]]s which uses an atomic counter to track how many people are accessing the data at once.

A semaphore is given a starting number which can be increased or decreased. If the number reaches zero, any threads attempting to decrease it will block until the value increases again.

Defined: `kern/thread/synch.c:43`

## Functions

### `P` (decrease)
Decrease the number contained by the semaphore, if possible (number > 0). Otherwise wait for the number to be increased.

### `V` (increase)
Increase the number contained by the semaphore. Notify all waiting threads that the number was increased.