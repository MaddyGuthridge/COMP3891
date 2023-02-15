```c
void spin_lock() {
	// Loop until unlocked
	while test_and_set(lock);
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
	    val = true;
    }
    return val;
}
```

Because the `test_andset` operation is atomic, this is [[thread]]-safe.

* Uses "busy waiting" - wastes CPU cycles while waiting
* Makes no sense on a single-CPU machine