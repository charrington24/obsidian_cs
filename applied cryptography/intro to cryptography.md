
#cryptography 
**encryption**: way of scrambling data in an unscrambleable way
it's really annoying to keep thinking of new ways to scramble, so we decided on one algorithm that just requires a "key" parameter

Secret key cryptography:
	- two inverse functions: encrypt and decrypt
	- authentication: if your secret key is 5 and the encryption algorithm is multiplication, someone can ask you to encrypt 12 to verify your identity. if you generate 60, then the other party knows you're legit without you having to divulge the secret
	- **integrity check:** function of message and key k. this is a checksum or a CRC or something
	- MAC (Message Authentication Code) is how we do integrity checks 
		message and key together generate the MAC
		then the message, key, and MAC are checked together to generate yes/no validity

Computational Difficulty
	- with a good encryption algorithm, attacker has to brute force through 2^n keys, whereas valid user only has to run O(n)
	- faster computers is better for the valid users- they can use longer keys without sacrificing performance, but the brute force length increases exponentially

XOR with random string as long as message as key is a possible secret key algorithm. this is possible but inconvenient

Private(?) key cryptography:
	analogy:
	- alice puts a lock on her box and sends it to bob
	- bob gets it, puts his own lock on, and sends it back
	- alice takes her lock off and sends it back to bob
	- bob gets the box back with only his lock on it, and so he can unlock it
	Alice sends msg XOR S_a, bob sends back msg XOR S_a XOR S_b, alice sends back msg XOR S_a XOR S_b XOR S_a = msg XOR S_b, and bob XORs it to msg
	problem with XORing is that if you XOR all 3 messages, you get the original message

probability of modifying message is function of length of integrity check and length of key

encryption history:
	caesar cipher
	monoalphabetic substitution

Public Key Cryptography
	aka "asymmetric cryptography"
	two keys that are inverses of each other
	you have a public key and a private key which are inverses of each other
	everyone knows bob's public key, but only he knows his private key
	you encrypt for bob using bob's public key, and he decrypts it with his private key
	analogy: nobody knows how to do division; they only ever invented multiplication

Non-repudiation: 
	if alice signs something, she can't later say it wasn't from her
	Done w public key digital signatures so that bob can prove to a third party to 
	Can't be done with MAC because MAC depends on secret only known to alice and bob, not a third party. 
	
[[cryptographic hashing]]

Random Number Generation
	- number doesn't really need to be random, it just needs to be hard for an attacker to guess
	- cryptographically random: hard to guess
	- RNGs embedded in popular programming languages are often deterministic
	- statistically random is different from cryptographically random
	- source of randomness: **seed**. also known as **sources of entropy**
		- strength of RNG no stronger than strength of seed
		- lots of non cryptographic RNGs use time of day or programmatic keystrokes. These are fine for running simulations but not good for cryptography
	- Geiger counter clicks, background noise on mic are good sources of microphone. Pretty sure cloudflare does this with lava lamps
	- Bits of entropy counted as log_2(g) (where g is # of guesses it'd take to find the value)
	- pseudo-random number generator takes seed + internal state and generates arbitrary length string of pseudo-random bits
	- attacker could get access to internal state, which would allow all future "random" output to be predicted
	- internal state allows you to keep inputting the same seed and get different results
		- generally you don't re-input the seed; the internal state is updated based on some rule with every generation, which allows 


