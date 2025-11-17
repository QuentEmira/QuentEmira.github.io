Modular arithmetic is just a reference to the mathematical operations done with the mod operator. For what I studied, these are the important parts.

```
(a+b) mod n = ((a mod n) + (b mod n)) mod n
(a-b) mod n = ((a mod n) - (b mod n)) mod n
(a*b) mod n = ((a mod n) * (b mod n)) mod n
```

These rules are used to solve problems of [[Fast Exponentiation]].