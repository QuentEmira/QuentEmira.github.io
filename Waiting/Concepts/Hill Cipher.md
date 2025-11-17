Hill cipher is a [[Block Cipher|block cipher]]. The size of the block is decided by the size of the key.
The key is a n x n matrix, where n is the size of the block.

The way the cipher is done is simple.
```
1. First, we separate the text based on the block size.
2. Next, we convert them into their ASCII values, and the mod 26 them.
3. So, if we have 'tin', and the key size is 3, it would be 116 105 110, which in turn gives us 12 1 6
4. Then, we matrix multiply the row with the matrix, in the same order.
5. The resultant row, mod it with 26.
6. Do this for all groups, and that will be your encrypted text.
```

For Decryption, the key will have to undergo a transformation, where we need to get the inverse of the key.
To get the inverse of the key:

1. Find the determinant of the key matrix.
2. Then, find the multiplicative inverse of the determinant.
3. After this, find the adj of the matrix
	1. First we need to expand the matrix
	2. $$\begin{bmatrix}a11&a12&a13 \\ a21&a22&a23 \\ a31&a32&a33 \end{bmatrix}$$
	3. To expand, first repeat the first two columns, extending to the right, and then repeat the first two rows, extending downwards
	4. $$\begin{bmatrix}a11&a12&a13&a11&a12 \\ a21&a22&a23&a21&a22 \\ a31&a32&a33&a31&a32\end{bmatrix}$$
	5. $$\begin{bmatrix}a11&a12&a13&a11&a12 \\ a21&a22&a23&a21&a22 \\ a31&a32&a33&a31&a32 \\ a11&a12&a13&a11&a12 \\ a21&a22&a23&a21&a22 \end{bmatrix}$$
	6. Next, remove the first row and column of the matrix.
	7. $$\begin{bmatrix}a22&a23&a21&a22 \\ a32&a33&a31&a32 \\ a12&a13&a11&a12 \\ a22&a23&a21&a22 \end{bmatrix}$$
	8. After this, we will start filling the new matrix. We will fill them row by row. For this, we will be going column by column in the original matrix. So the first column in the expanded matrix is mapped to the first row for the new value.
	10. For the first value, find the determinant of the 2x2 matrix where the first element in the first column is the top left element. Then, multiply this value by $(-1)^{i+j}$ where i and j are the row and column value respectively.
	11. $$\begin{bmatrix}a22&a23 \\ a32&a33\end{bmatrix}$$
	12. Next for the second value, find the determinant of the 2x2 matrix where the second element in the first column is the top left element
	13. $$\begin{bmatrix} a32&a33 \\ a12&a13\end{bmatrix}$$
	14. For the third value of the row, determinant of 2x2 matrix, where the 3rd element of the 1st column is the top left element.
	15. $$\begin{bmatrix} a12&a13 \\ a22&a23 \end{bmatrix}$$
	16. Now, we got the value for the first row. Next, for the second row, do the same with the second column.
4. Another way to find the ADJ is just to find the cofactor matrix, and take the transpose of that value.
5. After this, multiply the adj with the multiplicative inverse, and we get the inverse of the key matrix. mod 26 all values.

After you get the inverse key matrix, in order to decrypt, do the same thing you did for encryption, but instead of plain text, use cipher text. mod 26 the values to make sure the range is with the alphabet.