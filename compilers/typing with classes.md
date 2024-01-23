#compilers 
extension of [[type checking]]
error class covered in [[error type]]
### Properties of Inheritance Structures
- Reflexivity: any type is convertible to itself
- Transitivity: A convertible to B and B convertible to C, then A convertible to C
- Antisymmetry: If A is convertible to B and B is convertible to A, then A and B are the same type
- These three rules combined form a partial order over types
- Dope new rule for assignments that passes this code: 
	`Base myBase;`
	`Derived myDerived;`
	`myBase = myDerived;`

- ![](https://lh7-us.googleusercontent.com/csbpFZVE-XLJ6cDTFY9bw356J9maVEQnq6YMdDSwvUnGRPQH0HYtvpxA5A-r4iSU7IIW6nkuD92tYlxsUk7L5m9vJdNlK9dZOnDlizHvLFlN55t-zgM6z7vEq-wK3JhOlTvQaQ9XGy-drFw6WBKBH9k)
- Inferring to T2 is ideal because it keeps the type as specific as possible (If you derived to T1, you could have every type resolve to Object in Java, for example). We want to propagate types as precisely as possible
### Updated Rules 
- we need to update our previous rules to cover cases with type inheritance
- Comparisons: 
- ![](https://lh7-us.googleusercontent.com/H_K4dMXvNKsJOph0dlEsfr8W9_4_MN4iXP2KG5yoP8n24e2AY2wmPQVbCCIZGIIJBaaS93v8HU3Cw07ZUxMrZ2c3eJ4mBmZS4TtG0r3UtcdhAKJH0KSuiz5Vq79-y7GkV10oz158sLJKtm-o0hydJHo)
- Function calls: 
- ![](https://lh7-us.googleusercontent.com/8GZkL9d39FMhIu4FANphDTcHX0iYo1jvyDWg99O9RvK5UkTGFikBcf-UZz0dyVEw2cUXZPVfyqhjnpwJoEnlxcGWFQPfqpvTAHgq-xHym-5xHcaIEShioCMKPRGm6r9TgWSBpFTSQEYob68DeBe_GbU)
- in basic words: each arg must be a subtype (or the exact type) of the type declared. Less restrictive than requiring exact match for each type

### Types and Partial Orders
- A <= B means A is convertible to B
### Handling null
- Give programmer access to a null literal; behind the scenes, the compiler defines a null type at the bottom of the type hierarchy. 
- null type is convertible to any class; null <= A
### Nuances (Conditions)
- example: ternary conditional operator ? :  (if statement shorthand)
- how to type check an expression containing this operator?
	`S |- cond : bool`
	`S |- e1 : T1`
	`S |- e2 : T2`
	`T1 <= T2 or T2 <= T1` 
	`____________________`
	`S |- cond ? e1 : e2 : max(T1, T2)`

- above rule does NOT WORK because what if T1 and T2 are siblings in the hierarchy? (Both derived from base)
- Base = random() ? new Derived1 : new Derived2;
- we need to type the result as the least upper bound of the possibilities (denoted as T = T1 V T2)
	`S |- cond : bool`
	`S |- e1 : T1`
	`S |- e2 : T2`
	`T = T1 V T2`
	`____________________`
	`S |- cond ? e1 : e2 : T`

### Upper Bounds
- upper bound: some common ancestor of two types 
- least upper bound: least (most recent) common ancestor
- becomes messy with multi-inheritance (because type hierarchy is no longer a tree)
- You can restrict the language to disallow multi-inheritance but it’s pretty common (C++, Java)
- minimal upper bound: minimal upper bound C of types A and B would be a C such where C is an upper bound of A and B and there exists no upper bound of A and B C’ below C (nothing lower than C is an upper bound).
- Not necessarily unique
- Least upper bound is always minimal, but minimal is not always least
- in comparison, least upper bound is always unique
- so the most goated rule is this: 
	`S |- cond : bool`
	`S |- e1 : T1`
	`S |- e2 : T2`
	`T = minimal upper bound of T1 and T2`
	`____________________`
	`S |- cond ? e1 : e2 : T`
- allows us to propagate that the result can be either type: Base1 or Base2
