#algorithm 
#compilers 
### Maximal Munch
- Take the maximum length of match until an error is found. 
- Take as many transitions as possible. When out of characters, or a transition does not exist for the next character, backtrack to the last accepting state.
- Example - ‘fortress’ would be considered as an IDENT even though for tress can be separate FOR and IDENT tokens

### Simplified Maximal Munch
- Consume characters until tokens are exhausted or there is not a valid transition. The key difference is that the Simplified Max Munch does not back track i.e. if “call” and “do” are valid, but “calldo” is not valid, Max Munch would give two valid token “call” & “do” where Simplified Max Munch reads an invalid token “calldo”.
- Example of MM vs SMM: 
- Language: {a, b, abc}
- Input: ‘ababc’
- Max Munch: start @ ‘a’, continue to ‘b’, but fail to transition to ‘a’. Backtrack and accept ‘a’, followed by ‘b’. Finish by accepting ‘abc’
- Simplified Max Munch: start @ ‘a’, continue to ‘b’, but fail to transition to next ‘a’. Report an error and fail to match anything. 
- Example - A grammar consists of tokens INT_VAL = ["-"] digit { digit }, PERIOD = ".", FLOAT_VAL = INT_VAL "." digit { digit }, and ERROR, where digit = "0" | "1" | ... | "9". Given the input string "1.-4", maximal munch would consume the "1", then consume the ".", then would have no valid transition with the "-". Maximal munch would backtrack to the last accepting state: "1". This would result in an INT_VAL token being output. The PERIOD token would then be output, and then another INT_VAL token. With simplified maximal munch, the "1" and "." would be consumed as valid transitions. When the "-" is reached, there is no valid transition. The algorithm then checks if the currently accumulated string is valid. "1." is not valid, so an ERROR token is output. An INT_VAL token would then be output (assuming the rest of the string is not thrown away as an error).
- Maximal Munch: INT_VAL PERIOD INT_VAL
- Simplified Maximal Munch: ERROR INT_VAL
