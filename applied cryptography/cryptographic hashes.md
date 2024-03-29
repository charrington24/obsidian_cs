#cybersecurity 
#cryptography 
- **cryptographic hash**: takes arbitrary-sized bitstring and outputs a fixed-size bitstring
- security properties:
	- **first-preimage resistance**: no easier way than hashing randomly chosen values to find input whose hash equals some specified value
	- **collision resistance**: no easier way than hashing random values until you find two inputs whose hashes are equal
	- **second-preimage resistance**:
	- hash needs to be reasonably big (128 bits) and look random to have these two properties
- finding a collision is easier than finding a preimage 
	- the birthday problem explains why this is
- what can you do with a hash?
	- digital signature (RSA)- don't sign msg, sign hash
	- password database- you can store hashes instead of plaintext (improved w salting)
- Hash chains
- Lamport's hash (aka S/Key)
	- Bob's database stores for each user:
		- n, salt, hash^n+1(pwd | salt)
	- alice sends i'm alice
	- bob sends n, salt
	- alice sends hash^n(pwd | salt)
	- bob modifies db to store hash^n
	- this offers eavesdropping protection and server database reading without public key cryptography
	- someone can impersonate bob- request a very small n. this is **small n attack** 
- Puzzles
	- Force a party to do a lot of work by asking next message to have a hash with first k < n bits of hash equal to some value x
		- work grows exponentially with k
		- alice to bob: do something
		- bob: Ok, tell me a number whose hash ends with 35465789
- Blockchain
	- append-only log consisting of a chain of blocks
	- in each block, include hash of previous block
	- this means you can't easily change log entries, since all subsequent blocks depend on previous hash
	- you can also maintain a "ledger" - save hash value every 10 blocks to some external protected location
	- if you find the valid next block as a "miner", you get rewarded with Bitcoins
	- valid block consists of new valid transactions, a random number, and having a small enough hash value
	- this is basically like winning the lottery
	- can make it harder by making the required hash smaller
	- we want a new block every 10 minutes- there's an algorithm that adjusts the # of leading zeroes required to make this happen
- Bit commitment 
- Hash Trees (Merkle Tree)
	- way to hash together large amounts of data such that the hash value can be confirmed without reading entire file
- How to create hash function?
- 