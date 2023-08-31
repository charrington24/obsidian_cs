![[Slides03-Top Down Parsing.pdf]]
#compilers 
- **top-down parsing**: start symbol, try to guess productions to apply
- **bottom-up parsing**: begin with program, try to reduce to the CFG
- you can imagine parsing as a blind graph search, where each node is a possible derivable form (each node's children are the forms derivable from the node)
- doing it with BFS- lots of time and memory. High branching factor and generates a lot of unused sentimental forms.
- We can optimize BFS by restricting it to leftmost derivations only. Work on all grammars
- Issues with leftmost BFS: often not the optimized path
- How about leftmost DFS?
	- advantages: lower mem, high performance
	- disadvantage: only works on grammars WITHOUT left recursions
		- A->Aa|c
		- try to get to c from A
		- A->Aa->Aaa->Aaaa etc. Never c