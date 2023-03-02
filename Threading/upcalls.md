Used to signal to a program that one of its threads has blocked, allowing that program to choose another user-level thread to take over.

## Kinds of upcall

- **New**: allocated a new "virtual CPU"
- **Blocked**: a thread has blocked and the user-level scheduler can pick a new thread to take over
- 