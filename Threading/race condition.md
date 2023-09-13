When two [[thread]]s are accessing the same data, it can cause a race condition. This happens if one thread writes to the data, while the other thread doesn't expect it to change, causing bad results.

```c
void inc(int *num) {
    // Load the value
    int value = *num;
    // Increment it
    value++;
    // Store it
    *num = value;
}

void dec(int *num) {
    // Load the value
    int value = *num;
    // Decrement it
    value--;
    // Store it
    *num = value;
}
```

In the above code, both functions run simultaneously. A race condition is caused if the value is written by one while the other is operating on the old value, since that means the new value will be overwritten by the first thread.