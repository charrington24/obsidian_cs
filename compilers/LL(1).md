#compilers
- Left-to-right, Leftmost derivation, 1 lookahead symbol
- LL(1) grammars must be unambiguous
- This means that if a grammar is ambiguous, it cannot be LL(1)
- This does NOT mean that an unambiguous grammar is LL(1)
- No collisions on the Parse Table
- This could include a First-First, First-Follow conflict
- **First-Follow Conflict**: If a nonterminal has an epsilon transition, and some character ‘c’ exists in BOTH the FIRST and FOLLOW sets, there is a conflict.
	- Intuition: Due to the epsilon transition, parser cannot decide between using FIRST or FOLLOW set to determine next production.
- **First-First Conflict**: If a nonterminal has production rules with non-disjoint FIRST sets.
	- Intuition: If two or more productions for the same nonterminal have a common terminal in their FIRST sets, 1 lookahead symbol cannot be used to determine which production must be taken.
- If your CFG isn’t LL(1), you can do the following (in order):
	- Eliminate Left Recursion if it exists
	- Eliminate Epsilon if it exists by expanding it to all possible states
- EX { A-> AaA | ε } converts to…
	- A -> AaA | Aa | aA | a
	- This was done by subbing in epsilon.
	- { A -> Aa₁ | Aa₂ | b₁ | b₂ } converts to…
	- A -> b₁A’ | b₂A’
	- A’ -> a₁A’ | a₂A’ | ε
- NOTE: b is any string that doesn’t have the nonterminal to the left of it
- Left factor if necessary:
	- ie. {A -> aA | aB | a} converts to
	- A -> aA’
	- A’ -> A | B | ε
- Converting to LL(1) Examples

![](https://lh7-us.googleusercontent.com/k-Xxfst_IJ6SYFhfK9aZSa29df1rmKO8H_D7DV64ewKVfX6voWHZZnmR0jlGW3x-D6fdtU80YHeSXsY6Mg93JKzZd8POy68CI3sg4ADw7fp5V8HSXwBzkKaiFM4gWOp2XYsaiAQjmcx4le7p6fuXpj8)
