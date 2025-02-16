This is a modification of the [[Euclidian Algorithm]]. This algorithm is primarily used to find the Multiplicative Inverse of a number, with respect to another number. The method is mentioned below:

| Q   | A   | B   | R   | T1  | T2  | T0  |
| --- | --- | --- | --- | --- | --- | --- |
| 1   | 5   | 3   | 2   | 0   | 1   | -1  |
| 1   | 3   | 2   | 1   | 1   | -1  | 2   |
| 2   | 2   | 1   | 0   | -1  | 2   | -5  |
|     | 1   | 0   |     | 2   | -5  |     |
- First, take a and b to be the numbers, with a being the bigger one..
- Next, assume that t1 is 0, and t2 is 1.
- Calculate Q and R. Then, calculate T0. ( $T0 = T1 - (T2*Q)$ ).
- After this, create a new row, and assign the following for values:
	- A = B
	- B = R
	- T1 = T2
	- T2 = T0
- Now, if B = 0, then the value in T1, in that row, is the multiplicative inverse. In the case that the value is negative, just add first B value to it.
- If you are wondering, the value at A will be your GCD.