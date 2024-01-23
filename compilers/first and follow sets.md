#compilers
used in [[top-down parsing]]
related to [[LL(1)]]
### First Sets
- The set of terminals which may begin a string that can be parsed by a non-terminal. 
- Assume we have a rule like X -> …. 
- Then FIRST(X) would contain the first terminal T
- If FIRST(NT1) contains ε and FIRST(NT2) does not contain ε, FIRST(X) would contain FIRST(NT1)\ε U FIRST(NT2)
- If FIRST(NT1), FIRST(NT2), FIRST(NT3), … FIRST(NTn-1) contain ε, FIRST(X) would contain FIRST(NT2)\ε U FIRST(NT3)\ε U … FIRST(NTn-1)\ε 
- If FIRST(NT1), FIRST(NT2), …. FIRST(NTn) all contains ε, FIRST(X) would contain FIRST(NT1)\ε U FIRST(NT2)\ε U … FIRST(NTn) U ε

Example 1:
	A -> BCD 
	B -> ε | hB 
	C -> g | i
	D -> d 
	
	FIRST(A) = FIRST(B)\ε
	FIRST(B) contains ε, so FIRST(A) = FIRST(B)\ε U FIRST(C) 
	FIRST(C)  = {g, i} so FIRST(A) = {h, g, i}

Example 2:
	A -> BCD 
	B -> ε | hB 
	C -> g | i | ε
	D -> d
	
	FIRST(A) = FIRST(B)\ε
	FIRST(B) contains ε, so FIRST(A) = FIRST(B)\ε U FIRST(C) 
	FIRST(C) contains ε, so FIRST(A) = FIRST(B)\ε U FIRST(C)\ε U FIRST(D)
	FIRST(D) = {d} 
	Therefore, FIRST(A) = {h} U {g, i} U {d} = {h, g, i, d}

Example 3:
	A -> BCD 
	B -> ε | hB 
	C -> g | i | ε
	D -> d | ε
	
	FIRST(A) = FIRST(B)\ε
	FIRST(B) contains ε, so FIRST(A) = FIRST(B)\ε U FIRST(C) 
	FIRST(C) contains ε, so FIRST(A) = FIRST(B)\ε U FIRST(C)\ε U FIRST(D)
	FIRST(D) contains ε, so FIRST(A) = FIRST(B)\ε U FIRST(C)\ε U FIRST(D)\ε U ε
	
	Therefore, FIRST(A) = {h} U {g, i} U {d} U ε = {h, g, i, d, ε}

### Follow Sets
- The set of terminals that can immediately come after a given non-terminal from a derivation starting from the start symbol
- FOLLOW sets are additive. Every production where some nonterminal occurs may add to that nonterminal’s FOLLOW set.
- [University of Alaska Explanation](https://www.cs.uaf.edu/~cs331/notes/FirstFollow.pdf
	1. Place $ in FOLLOW(S), where S is the start symbol and $ is the input right endmarker.
	2. If there is a production A ⇒ αΒβ, then everything in FIRST(β), except for ε, is placed in FOLLOW(B). If FIRST(β) has ε, then FOLLOW(B) contains FOLLOW(A) (SEE RULE 3).
	3. If there is a production A ⇒ αΒ, or a production A ⇒ αΒβ where FIRST(β) contains ε (i.e., β ⇒ε), then everything in FOLLOW(A) is in FOLLOW(B)
	4. If there is a rule A -> B, FOLLOW(B) contains FOLLOW(A).
- Interesting Example:
	- A → B C D
	- B → h B | ε
	- C → C g | g | C h | i
	- D → A B | ε

|   |   |   |
|---|---|---|
|Non-Terminal|FOLLOW|Explanation|
|A|h $|[First(B) + usual $]|
|B|h ε|[First(C) + Follow(D)]|
|C|g i|[g, h, First(D) + Follow(A)]|
|D|h g i ε|[Follow(A)]|

### Parse Table
- Relates an input token with the grammatical rule that derives it.
- Allows for finding syntax errors: If a token is found that has no grammatical rule to derive it, that is a syntax error. 
- This happens when the spot on the table is empty
- Steps of populating the table:
- Make a table with:
	-  a row for each non-terminal
	-  a column for each terminal and $ 
- Generate a First set
	- For each terminal in the first set, put the production rule associated with
	- If there is an ε anywhere in the CFG, generate a Follow set
	- If a production rule has Ɛ, the characters from the Follow set are included in the parse table
- Example: Given A -> +BA | Ɛ, FIRST(A) = {+, Ɛ}, FOLLOW(A) = {$, )}, both + and ) are included as rules in the parse table