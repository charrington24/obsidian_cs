more in [[function overloading]], [[type checking]], [[typing with classes]]
#compilers 

- Rule for member functions:
 ![](https://lh7-us.googleusercontent.com/NJE-diXhgSryFXBL8A9zJsWdwZiAGQAi2KklIcU8gwSt-DOdnfiZeDVfUs2A8zQf0qyZMLYhxij27Zq2V4NFxaBmpKHkyRe1KKCGcL50M1b534ccwxgTbJ5mrqTvKVGpPFFUFrwGYDs4B1DADiMt6PA)
- legal: good program, will run
- safe: passes static type checking
- static type: declared in program source
- dynamic type: actual object type at runtime
- no way to write a perfect type checking rule
### Soundness and Completeness
- static type systems often incomplete: valid programs rejected
- we want it to be sound: not allowing bad programs to pass
- try to prove that DynamicType(E) <= StaticType(E) for every expression 
- our type system is sound and incomplete
- there does not really exist a type system that is both sound and complete
### Covariance and Contravariance
- covariance: can assign More Derived to Less Derived (Lower to Higher)
- contravariance: can assign Less Derived to More Derived (Higher to Lower)

|   |   |   |
|---|---|---|
||return type|argument type|
|covariant|safe (return type of A convertible to return type of B)<br><br>  <br><br>![](https://lh7-us.googleusercontent.com/ThZ_myA7baUB8tx6-DxV_DpTCQ1Xkw-ybUSVJ5vrRbpCzPiKVBpWnX3cIhYPsz4HJnG5KjNFcMFkVpSEMktBWSibEgSx0RkQtyzAqnASYzoiT7jINZ47iJaEvzjxUT4sD6fdCo4_Hi_V-d--PGdzM-I)|Unsafe<br><br>  <br><br>![](https://lh7-us.googleusercontent.com/vcjaJwiJNfb1TuLUUubU7lO4kWp0WiylJk3LQ-joK1uFpMAe9CgvQjjkSTWoSTkdkDj4uYhshgopTmwZeC-l9VsbT1aqtYeeB7hAe6IYxbxYocI5YrUE9AtUws8OIuQsSqYEciM_maBH6lBUmO08O2c)|
|contravariant||safe (but rarely supported)<br><br>![](https://lh7-us.googleusercontent.com/R6I8OMuiNVIcnriig3s5SNfufonb5ySYYZf_dy3Ss4zi_tUhfSCpPTqBhRsz8AcbL2zw5qWN0enY9JodgyC8E7CAVNeES1d0nHFxEieMgXbsJBYDsmLgCbsvQqhp-cIqN6-9qL3cOdB2nkBsmIlval4)|