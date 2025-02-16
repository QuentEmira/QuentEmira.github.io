Chinese Remainder Theorem is a way of finding a number, given we have the remainder the number given with different numbers. I will describe the method below:
```
Given:
x = 2 mod 3
x = 3 mod 5
x = 2 mod 7

We need to find x.
1. First find the product of all the divisor. 3*5*7 = 105.
2. Next, find the M_i values for each divisor. This will be just the product divided by the divisor. So, for 3, its 35, for 5, its, 21, and for 7, its 15.
3. After this, find the multiplicative inverse of the M_i, for their corresponding divisor value. 
4. So, 35*b = 1 mod 3. here b = 2.
5. 21*b = 1 mod 5. here b = 1
6. 15*b = 1 mod 7. here b = 1
7. Finally, for each divisor, multiply the inverse, the M_i value, and the remainder. Then, sum all these products.
8. f = 2*35*2 + 1*21*3 + 1*15*2 = 233.
9. Next, mod this result with the total product. That will be your x.
10. 233 mod 105 = 23.
11. x = 23
12. 23 = 2 mod 3
13. 23 = 3 mod 5
14. 23 = 2 mod 7
```

