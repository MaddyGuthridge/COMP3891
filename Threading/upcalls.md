Used to signal to a [[process]] that one of its threads has blocked, allowing that program to choose another user-level thread (see [[scheduler activations]]) to take over.

## Kinds of upcall

- **New**: allocated a new "virtual CPU"
- **Blocked**: a thread has blocked and the user-level scheduler can pick a new thread to take over
- 