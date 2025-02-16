To understand this, first we need to understand the [[Division Algorithm|division algorithm]].

- The Euclidean Algorithm is a method to find the GCD between two numbers.
- The method is explained below:
```
1. First, take the two numbers, a and b, with a being the bigger number than b
2. Next, find the value of q.
3. After this, calculate bq, and subtract this from a to get r.
4. Repeat the whole process, with a = b, and b = r.
5. Stop when r = 0. Then, b is the GCD.
```
- The intuition behind this method is simple. If we take the GCD between two  number a and b to be x, then
```
x|a and x|b.
We kow a = bq + r
because a is divisible by x, (bq + r) must also be divisible by x. This means that both bq and r need to be divisible by r.

already, we know that x divides b, so bq is handled.

By extension, r must also be divisible by x. Due to this, instead of just finding the gcd between a and b, we can directly find the gcd between b and x, which would be much simpler.
```

There is an modification of this, called the [[Extended Euclidean Algorithm]]