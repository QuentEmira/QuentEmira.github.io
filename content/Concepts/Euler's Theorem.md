First, we need to understand Euler's Totient

## Euler's Totient Function

Euler's Totient function gives the count of the number of values that are lesser than the given number and are co prime to that number.

Φ(9) = 6  (1,2,4,5,7,8)

There are some ways to easily calculate Euler's Totient function value
1. If n is a prime, then Φ(n) = n-1. So, Φ(11) = 10.
2. If n is not a prime, then Φ(n) = product of totient values of its prime factors. So, for Φ(10) = Φ(2) * Φ(5) = 1 * 4 = 4 (1,3,7,9).
3. Φ($p^{h}$) = $p^{h} - p^{h-1}$

## The theorem
Based on the above, we can formulate the below theorem.
$$a^{Φ(n)} \equiv 1\ \textrm(mod\ n)$$
This can be used in fast exponentiation, and in finding the inverse of a number.