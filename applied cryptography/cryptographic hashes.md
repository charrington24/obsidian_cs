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