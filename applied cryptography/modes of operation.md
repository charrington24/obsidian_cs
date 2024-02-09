#cybersecurity 
#cryptography 
NOTE: i missed the first 45 minutes of this lecture- chapters 4.0-4.25 in book. need to go back and fill these notes in

sections missed: 
introduction
encrypting a large message
notes on large message: you come up with a secret key, encrypt the message w secret key, encrypt the key with bob's public key
### Generating MACs
- CBC Residue- it's as though you're encrypting a message, but you take the last block and use it as the checksum
- if the message is not a multiple of the block size you can add padding
- if you don't know whether the msg is multiple of block size, you can add in a full block of padding. But that's inefficient
- so there are two versions of CBC-MAC depending on whether there's a final block of padding

CBC Residue
- how to force a particular residue?
- decrypt desired CBC residue, XOR it with message, keep working backwards

