#cybersecurity 
#cryptography 

- newer public key algos; some can only do signatures or encryption, but RSA can do both
- quantum will probably make these unsafe in the next 5 years
	- a large quantum computer could run **Shor's algorithm** to factor numbers (break RSA) and do discrete logs (break Diffie-Hellman)
- each user (**principal**) has two complementary keys: private and public
	- signatures: sign with private and verify with public
	- encryption: encrypt with public and decrypt with private
- should be infeasible to calculate private key given known public key