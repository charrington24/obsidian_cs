#compilers
extension of [[type checking]] and [[typing with classes]]

- overloading: same name but different set of arguments
- while type checking, need to determine which function is meant and report error if no function matches
- Begin with set of overloaded functions, filter out functions that cannot match; this leaves us with a candidate set (C++) or potentially applicable methods (Java)
- need to pick most applicable function from candidate set
### Overloading with Inheritance
- how to rank which function is the best match?
- given two functions A and B, with arg types (A1… An) and (B1… Bn), A<: B if Ai <= Bi for all i 1<= i <= n. Basically: we want the most specific types (lowest in hierarchy).
- A function is best match if A <: any other candidates.
- If there’s no best match, we get ambiguity
### Ambiguous Calls
- Example:
	`void F(Base b1, Base b2)`
	`void F(Base b1, Derived d2)`  
	`void F(Derived d1, Base b2)`
- if we have `F(new Derived, new Derived)`, how do we resolve it?