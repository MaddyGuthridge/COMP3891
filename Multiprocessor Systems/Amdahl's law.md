Given a proportion of processing time $P$ that can be made parallel, and the remaining serial portion $1 - P$, the speedup by using $N$ processors is 
# $\frac{1}{(1 - P) + \frac{P}{N}}$ 

Limits can be used to determine the maximum performance. As $N \rightarrow \infty$, $\frac{P}{N} \rightarrow 0$, meaning our performance becomes limited by $1 - P$.
