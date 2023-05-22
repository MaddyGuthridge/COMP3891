## Batch systems
- No users directly waiting - they submit a job and come back in a few days
- We just optimise for overall machine performance - no need to care about things being responsive
- Used for systems like build servers and supercomputers

## Interactive systems
- Users need their system to be responsive
- We need to make everything perform well enough that everything continues to feel snappy
- Used in most desktop [[operating system|operating systems]].

## Realtime systems
- Jobs have strict deadlines
- We need to make sure that these deadlines are met, since otherwise things will break
- Used in performance-critical systems (such as aircraft autopilots)