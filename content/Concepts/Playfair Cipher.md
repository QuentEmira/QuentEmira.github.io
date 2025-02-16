This is a cipher that works on two letters at a time. It is a [[Symmetric Key Algorithm]], and also a [[Block Cipher]].

For this cipher, we will need a key, which should be a string.
In general, the key used in this 'MONARCHY'.

Follow the below steps for the Playfair cipher.
1. First, generate a 5x5 matrix that will be used in order to encrypt the text.
	1. First, draw out the matrix.
	2. The matrix will be filled with letters. Because there are 26 letters, but only 25 spaces, i and j are grouped together.
	3. First, from the top left, row wise, fill out the cells with the letters in the key, making sure not to repeat any letter. After this, fill out every cell with the leftover letters in the alphabet, once again without repeating.
	4. $$
	\begin{bmatrix} M & O & N & A & R \\ C & H & Y &B &D \\ E&F &G &I/J &K \\ L&P &Q &S &T \\ U&V &W &X &Z \end{bmatrix}
$$
2. After this, divide the plain text into groups of two
	1. Make sure that the letters are not repeated in the pair.
	2. In the case that a pair has repeated letters, add and X in between.
	3. If the last letter has no pair, add X as pair.
	4. If the repeated letter is X, go for another letter.
	5. So, for helloz, it become HE_LX_LO_ZX
3. After that, take each pair and do the following.
	1. First see if you can create a mini matrix with the letters.
	2. Lets say for LX, we get the following matrix. $$\begin{bmatrix} L &P &Q &S \\ U &V &W &X \end{bmatrix}$$
	3. The above is a snippet from the 5x5 matrix. Now, L is in the top left, and X is in the bottom right. In order to encrypt it, just take the letter in the other corner, row wise.
	4. So, in our case, LX -> SU.
	5. In the case that the pair is in the same row or column, to encrypt substitute the current letter with the letter to the right / the letter below (row / column). Loop back to same row or column if there is no letter.
	6. So, if we are dealing with HP, HP -> FV.
	7. If it is HD, HD -> YC.
4. After every pair is encrypted, we get the cipher text.
5. To decipher, just reverse the above steps. Your decrypted text will have the letter X you might have added in between. This cipher does not encrypt spaces.