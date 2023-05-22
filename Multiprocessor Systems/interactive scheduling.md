Interactive [[scheduling]] is a category of [[scheduling algorithm]] which prioritises keeping the system interactive for the user.

Interactive schedulers are most-often used for consumer systems, such as desktop and mobile [[operating system|operating systems]].

## Minimising the response time
- Response time is how long it takes for a user to see the result of an interaction they give
- Response time is extremely important for making the system seem performant

## Proportionality
- The user expects short jobs (eg clicking a close button) will complete quickly
- They expect long jobs (eg running a compilation script) will take a while
- We should prioritise short jobs to make the system "snappy"
- It's ok if long jobs take slightly longer - the user won't care that much about a 1% penalty for a job that takes an hour