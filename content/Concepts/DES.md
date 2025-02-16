DES stands for Data Encryption Standard. This is a [[Block Cipher]]. It works with plaintext that has been broken down into 64 bit blocks. If the block is smaller, it is padded out with 0's.

## Structure
First, lets understand the structure of DES.
![[DES Overall Structure.excalidraw#^group=7Mm5mJY5|center]]
- This is the structure for DES. It contains two parts, the key generation, and the encryption.
- The encryption for DES happens in rounds. Each round gets its own key, and its plain text either directly, or from the previous round's output.
- The plain text is 64 bit. This first goes through an initial permutation, where all values are transposed.
- Next, this is sent to the round 1 function, along with the key.
- The output of this function, is sent to round 2, along with the key for round 2.
- This goes on till round 16. After that, the 64 bit text is sent to the 32 bit swap, where its divided in half and swapped.
- After this, an inverse initial permutation takes place.
- The result is the cipher text.

### Key Generation
![[DES Overall Structure.excalidraw#^group=-zTMZrJeqxWF0M97png7Q|center]]
- Key generation does not have much difference from the overall structure.
- First, we have the permuted choice, where 56 of the 64 bits are chosen and transposed around.
- Next, the 556 bits are divided into two 28 bit values. Each value under goes a left circular shift.
- The amount by which it is shifted is decided by the programmer.
- After that, the 2 28 bits are sent to a permuted choice, where 48 bits are chosen and transposed around. This is the key for round 1.
- For round 2 key's permuted choice 2, the 2 28 bits come from a second left shift operation, whose input comes from the first shift operation.

### Round Function
![[DES Overall Structure.excalidraw#^group=E3nMQW88OCQPebzPp8fnQ|center]]
- The round function works with the 64 bit text.
- Divide this into two parts, left and right.
- Now, keep the left part aside.
- Take the right, and expand it using expansion permutation.
- XOR the expanded part with the key.
- Next, send it through s box substitution, where its size was decreased to 32 bit.
- Next, xor this with the left part.
- This will be your new right
- Your new left will be your old right.