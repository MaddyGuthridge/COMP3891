A spin lock is used to provide the most basic synchronisation, usually used at the very core of an [[operating system]] as a way to bootstrap other [[synchronisation primitive|synchronisation primitives]].

```c
void spin_lock() {
	// Keep trying to lock it until we succeed (it returns 0)
	while (test_and_set(lock));
	// When it returns 0, that means we own the lock
	critical_region();
	unlock(lock);
}
```

Where `test_and_set` is an atomic operation similar to as follows
```c
// Operation is atomic - this is a single CPU instruction
bool test_and_set(bool* lock) {
    bool val = *lock;
    // If unlocked, lock it
    if (!val) {
	    *lock = TRUE;
    }
    return val;
}
```

Because the `test_andset` operation is atomic, this is [[thread]]-safe.

* Uses "busy waiting" - wastes [[CPU]] cycles while waiting
* Makes no sense on a single-CPU machine, since we're not giving the other process an opportunity to release the lock

## Performance considerations
The implementation above, while simple, can cause problems on [[multiprocessor system|multiprocessor systems]], as the test and set operation requires exclusive control over the [[bus]] to prevent [[race condition|race conditions]]. A variation of a spin lock that doesn't lead to [[starvation]] due to creating a [[bottleneck]] in the [[bus]] is as follows:

```c
void spin_lock() {
  wait_for_unlock:
	// Only reading the value - since we're not writing, we don't need 
	// exclusive bus access
	while (lock);
	// Now the lock is unlocked, let's try and acquire it
	if (test_and_set(lock)) {
		// Oh no! We failed, let's go back and wait again
		goto wait_for_unlock;
	}
	// We acquired the lock, let's do our work
	critical_region();
	unlock(lock);
}
```
