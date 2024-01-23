#compilers 
### What is a Type?
- A set of values (does not have to be finite), and a set of operations on those values
- Type Errors occur when operations are performed on invalid types
### Types of Type-Checking
Static
- Never let bad things happen at runtime. 
- Analyze at compile time
- Generally more conservative. May prevent good programs from running
Dynamic
- Check type operations at runtime
- More precise, less efficient
No Type-Checking
- Just don't mess up
### Strong vs. Weak type checking
Strong
- Never allow a type error (Java, Python, JS, LISP, Haskell)
Weak
- Allow type errors at runtime (C, C++) but runs faster
### Logical Inference
- Work from bottom of tree and propagate type up![](https://lh7-us.googleusercontent.com/M-BMaZiT7MWceYY0IzIu2nte2HQc2BfDWSiSEi_FToipsLlfOR-TV93bLmrle5IakeCIWbtEAWwjXxsVy5952ymHCcoeT-38Ar_mQ2zZxwR6AD9qQufwMIjl1GD2-THm-krcpma4y-KJMkdu5GEecLg)
    
- Ex: two bottom leaves (bool y and bool true) are compared with ==
- have some rule that states (bool == bool) is of type bool
- this propagates up, we are then left with bool x == some bool, which is also bool
- Type inference is built from axioms and rules; ex: if e is an integer constant, then e has type int
### Formal Notation for Type Systems

![](https://lh7-us.googleusercontent.com/H7RtObFRGiXUL47C-Nmm4dVhEs9ksV7peyCe9j3_NH8UHls-d05fBJVcoGJmPGBy4XpgGrurrd18Fy61ereZlSOEuov7f0GSiJ-_997UFaYBpuFyWJs-1u1HsrHQFNRAk0ggA8tfq6F-KdpjicTO30g)

This is read “if preconditions are true, we can infer postconditions.”

![](https://lh7-us.googleusercontent.com/3J3TTo_4PpqhAMrDJ43xKFIoGkcxvO_5ADYk3pUAnFiQMjr_JaQLBFHuLwdzxHSnp8pAdKZkSkXbHVQIxvGak1Gnc9J1Qvx1KJ3p0GV9j1HTIwOG0NyEwAd2HmSaO2JtwJAWlplJaKBptL_peUH35U8)

if the expression e has type T.
The symbol ⊢ means “we can infer...”
### Simple Inference Rules
- rules for literals; structured like this: 

	i is an integer constant
	__
	|- i : int

### Examples of Formal Notations

![](https://lh7-us.googleusercontent.com/-sUq-qwapAoDfxgQqExPEhw2TzBMQ9taitH0HrjI2eAgYmbf0dwTTJFv9EGiKV8Zds5qJi9ikzw5iK6SD4YPcgoTKoMj_Wh8zSI6rincJvNtUTFfb4RwcF6jHG-hrDIgaQLTj910Cy6bBTqz1ugyokU)

### Adding Scope
- in practice, scope checking handled with symbol tables

![](https://lh7-us.googleusercontent.com/s6jwF_yl8dQmeyn_fgkSqPe0HxHJmuoTfqbmPBroxhenGWco5G6elx1SslhXrlvUoCS1MGYKsRg5G62eXWjrTB6d-fJYVo7aqJVMzX4nene2xGT7LhynrepQly7wNwJ0ezSnlj2Inu0aI0eps1T5WU4)

if, in scope S, expression e has type T.
Types are now proven relative to the scope they are in

![](https://lh7-us.googleusercontent.com/cyDtD5LV9suzU5OWwJM2Js7dFB_u9r1v8LvlkusTT4hbMAmF6ERzQR8lvt5hU2jaig3P6AJp0pbXzO2ddhn9PMOV4D3Fyiqxk4-MMbeutALXp0B8AsKELV0DqftYIThd82eeVhgq5oc98z_8w7bnddw)

### Rules for Functions

![](https://lh7-us.googleusercontent.com/8GZkL9d39FMhIu4FANphDTcHX0iYo1jvyDWg99O9RvK5UkTGFikBcf-UZz0dyVEw2cUXZPVfyqhjnpwJoEnlxcGWFQPfqpvTAHgq-xHym-5xHcaIEShioCMKPRGm6r9TgWSBpFTSQEYob68DeBe_GbU)

### Rule for Assignment

- Code can be type safe but still illegal; ex:
- if you have this rule:
		S |- e1 : T
		S |- e2 : T
		
		___________
		
		S |- e1 = e2 : T

- this code would pass the type checking: 
	`int x;`
	`5 = x;`
- and this code would fail:
	`Base myBase;`
	`Derived myDerived;`
	`myBase = myDerived;`
- this is legal, but would fail with the above rule
