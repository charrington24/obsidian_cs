more [[type checking]] and [[typing with classes]]
### Cascading Errors
- if you don’t define a propagatable type when you statically detect a type error, the error ends up cascading 
- deal with this by defining an error type
### The Error Type

![](https://lh7-us.googleusercontent.com/U5gUHdmBnsNTg4recXWbCXi24Q2Yk-XR24s1mMUOEzCbJZYJ33j29epAJqycCGyv2co7uxw-ANTdPnGdGIF4Mzf6DR5NaCqy8ycRYmBlRIZVt1VrOiRz5aM12h0qhnP1pzZXuJ7X6j81N7r5fNoY76k)

- lives at bottom of type hierarchy (even below null type)
- Propagates like this: `Error: Cannot compare Error with bool in practice**`