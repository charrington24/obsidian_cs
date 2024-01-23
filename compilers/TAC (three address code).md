form of IR (intermediate representation)
### TAC generation
- Done with recursive AST traversal
- Generate TAC for subexpressions and then propagate up
### For Expressions
- define some gen(e) : computes TAC for expression e
- store result in a temp, then return name of temp (basically just the counter number)
- maintain a counter that increments every time you introduce a temp, and use it to name temps (t0, t1… tn)
### Gen Functions

#### Basic Statements

![](https://lh7-us.googleusercontent.com/bxEkWvYnVEWxKY9kYKnZvHyyl26ioBr8o3U_3wNrN8amFs9BS4IYpE2PJLGQIUsPudy1MTkpkf2PNkZfbFXbpT4dR3ULtI9VwY77Tq83vV-dPOg3i-EpqmcVgSVnizCCYNclUoXW7yjCqqjTMiIS30g)
#### Simple Statements

- these do NOT return temp name
#### Conditional Statements

![](https://lh7-us.googleusercontent.com/-kJoQznFbUTC9wLcZ8REfu-joIrc6b3kuj5BbBoMPz0Mm6RdIhK72AEjM7rPPnrlQ_Wq74px8BcIgMMT32nCKnS9cwIaDHLPeSqZGqpU1D1pzcRN0M7NiLpuPBE27J3lvgW11DlGkxBNbtOHShJUhgM)

### Improving Gen functions
- currently we are generating (at least) one temp and one instruction per subexpression, which is inefficient
- easy improvement: don’t gen temporaries on leaf cases, just return the values immediately
#### Temporaries Recycling
- we can wrap temp assignments in code that increments and decrements the counter
- tldr: decrement counter once a temporary has been read
- ![](https://lh7-us.googleusercontent.com/K9hbd1JmoWA_1MovZCXEuDslqZXiyQndao2r5hlLYaaoPkle-H4oclltSq03v0q1o-oJq3Y8nquvo-9-Tc95w0zfZ3O6YpCwfePm6uL2QO2tclNKoWf_cgsuShpiUKvvGYSkXn-IS27YOLjS_UJ95qA)
    
