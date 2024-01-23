**

### Regex and Atomic Regex

- Used to describe regular languages
    
- Irregular languages: still formal, but can’t be described w regex, may require backtracking etc
    
- Regular expressions “atoms” (single regex units) combined with certain rules
    
- Kleene Closure: “*” 0 or more of the preceding atom
    
- *Unknown name*: “?” 0 or 1 (but not more) of the preceding atom
    
- 1 or more: “+” 1 or more of preceding atom
    
- Atoms can be grouped together using parentheses to form larger regex
    

- Example: “abc*” Each a, b, c is an atom. “(abc)*” “abc” is a single atom
    

- Operator Precedence: (R) -> R* -> R₁R₂ -> R₁ | R₂
    

### Implementation of Regex (Automaton)

Can be done with NFA or DFA- 

RE can be directly converted to NFA with E transitions  

### RegEx vs. automata

- Regex is declarative. Doesn’t offer a way to check that an input string matches the regex. Must be implemented in some way to use it as a tool.
    

- Human readable
    
- Can be implemented by deterministic and non-deterministic automata.
    

- Automata are operative. Can be used to validate an input string directly, but is not easy to read and derive the pattern/rule.
    

**