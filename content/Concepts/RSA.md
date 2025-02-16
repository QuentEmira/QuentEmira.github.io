RSA is an [[Asymmetric Key Algorithm|asymmetric key algorithm]], a [[Stream Cipher]], has public encryption and private decryption. It works by encrypting one letter at a time. RSA has two keys to work with, a public key and a private key. The public key is used for the encryption process, whereas the private key is used for the decryption process. Here is how RSA is done:
1. First, choose two prime numbers, p and q. These prime numbers are very important, and must not be easily findable. If we know even one of them, the encryption can be broken.
2. Calculate N, where $N = p * q$.
3. Next, calculate Φ(N). This would be Φ(N) = Φ(p) * Φ(q). [[Euler's Theorem]].
4. After this, we need the public key and the private key. The public key is of the form (e, N), whereas the private key is of the form (d, N).
5. Here, one must select the value of e. Make sure that e is co prime with the Φ(N).
6. Next, we need to calculate d. $1 = e*d\ \textrm(mod\ Φ(N))$. d is the multiplicative inverse of e.
7. Now we have everything to encryption. For encryption, take each character of the plain text and calculate. $CT = (PT)^{e}\ \textrm(mod\ N)$.
8. For decryption, for each letter in cipher text, calculate. $PT = (CT)^{d}\ \textrm(mod\ N)$.