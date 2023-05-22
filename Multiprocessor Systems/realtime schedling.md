Realtime [[scheduling]] is a category of [[scheduling algorithm]] which prioritises quick, consistent, and reliable response times.

Realtime schedulers are commonly used in performance-critical systems, such as aeroplane autopilots

## Deadlines
- Deadlines can be hard or soft
	- A hard deadline will have catastrophic consequences if it is missed (eg a plane crashing)
	- A soft deadline will be inconvenient but not irrecoverable if it is missed (eg a TV occasionally lagging while decoding video)
- We need to schedule our tasks so that they