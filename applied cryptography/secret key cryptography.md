#cryptography
### stream cipher
- seed (shared secret) fed into PRNG which are used as a one-time pad 
- pseudo-random number is not information-theoretic secure
### block cipher
- input is fixed-size block + key
- output is fixed size ciphertext block (same size as input)
- decrypt with ciphertext block + key
- what's a good block size? what about a key size?- block and key sizes don't necessarily need to be the same
- used in: 
	- DES (Data Encryption Standard)
	- 3DES
	- any secret key algorithm can be turned into a block cipher with a mode
- block cipher is fundamentally a mapping from an n-bit plaintext block to an n-bit ciphertext block
- How many possible 1-1 mappings are there from plaintext to ciphertext block with a 64 bit block? 2^64! (very large)
- this would require alice to use 2^64 \* 64 bits to tell bob which mapping to use
- instead, do mapping based on some smaller key
- change in each input bit should result in change in many output bits
#### practical block cipher design:
- should be indistinguishable from ideal block cipher, unless someone knows key
- use pseudorandom permutation
- needs to be reversible to allow decryption
- typical method is to do something not super secure but do it a lot of times
- each time you do it is called a **round**
- use different keys for each round, called **per-round keys**. made from main key- this is **key expansion**
- two types of transformations within a round:
	- s-boxes (substitution or confusion)
		- maps k bits of input to j bits of output
		- "randomly" chooses outputs
		- k and j must be small or lookup table would be insane
		- so s-boxes tend to be small
	- p-boxes (permutation or diffusion)
		- shuffles the bits around
