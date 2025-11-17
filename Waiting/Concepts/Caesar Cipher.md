Caesar Cipher is one of the earliest ciphers known to mankind. The logic behind this cipher is very simple. Given a plain text, each letter of the text is shifted by certain number, this number being the key.

For example:
```
Plain Text: Hello World

Key: 3

Cipher Text: Khoor Zruog
```

- Here, each letter is substituted by another letter that is 3 away to the right, from the letter. In case you reach the end, loop back to the beginning. So, Y gets encrypted as B.
- Caesar Cipher in general worked with the key of 3, but it can work with any key belonging to the set of number possible by $mod 26$ .
- When it comes to the characteristics of Caesar Cipher, it is a [[Symmetric Key Algorithm|symmetric key algorithm]], that work on each character one by one, like a [[Stream Cipher|stream cipher]].