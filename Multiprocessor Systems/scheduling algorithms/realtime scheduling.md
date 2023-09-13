Realtime [[scheduling]] is a category of [[scheduling algorithm]] which prioritises quick, consistent, and reliable response times.

Realtime schedulers are commonly used in performance-critical systems, such as aeroplane autopilots, and robots.

## Deadlines
- Deadlines can be hard or soft
	- A hard deadline will have catastrophic consequences if it is missed (eg a plane crashing)
	- A soft deadline will be inconvenient but not irrecoverable if it is missed (eg a TV occasionally lagging while decoding video)

## Predictability
- We need to schedule our tasks so that they meet their deadlines consistently
- By making the system predictable, software running on the system can behave more predictably (eg fewer buffer underruns in a video decoder due to the decoder getting consistent [[CPU]] time)


