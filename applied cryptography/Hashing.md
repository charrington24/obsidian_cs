#cryptography 
cryptographic hashes
- input: message of arbitrary size
- output: fixed size quantity
- should be efficient to compute hash but hard to find message from hash
- should also be **collision resistant**, meaning that it should be hard to find two messages with the same hash
uses of hashes:
- hashes make digital signatures practical- you can hash a message, then sign the hash instead of the message
	- important to note that once you've signed a hash, you've signed all messages that have that hash. this is why collision resistance is so crucial
- password hashing: store hashes 
