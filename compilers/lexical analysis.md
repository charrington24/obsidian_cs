#compilers
#csce434
#lecture
- these are lecture notes! slides here ![[Slides01_Lexical Analysis.pdf]]
- aka scanner
- tasks:
	- split string into characters
	- group characters into tokens (w h i l e into T_While)
- does not yet determine whether program is valid
- tokenizing:
	- piece of original program is called **lexeme**, which is turned into an enumerated type called a **token** 
	- some **lexemes** are discarded (eg whitespace), others have **attributes** that need to be stored
		- eg: 13 -> T_IntConst with 13 as an attribute
- associating lexemes with tokens:
	- tokens can be associated with one lexeme or many
- **formal language**: set of strings. many languages have finite descriptions; described using regex, automaton, or a grammar
	- regex: capture regular languages
	- can't be described with regex: irregular language