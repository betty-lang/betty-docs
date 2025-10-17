# None

`None` is a special data type, in terms of how it works in Betty. It is not one of the language's keywords and neither variables nor functions can be assigned it. 

Nullability support can be a rather controversial topic among language designers, as including support for it could potentially lead to a plethora of runtime errors, like when dereferencing null pointers.

What is more, extending a language to support null and nullable types can introduce a whole new layer of complexity (oftentimes unnecessary).

However, allowing implicit returns of a `unit`-like value (`None`, in our case) can be beneficial in handling cases like the default return value of functions. Betty is a dynamic language, therefore a single function can return multiple data types. Introducing a default return value mitigates a significant class of potential issues and ensures all code paths have a return value.

Under the hood, it is far more convenient to implement a visitor pattern in the interpreter, when all node visits result in the return of a uniform `Value` struct (with `None` as a potential value type). In this manner, there's no need for special handling of uninitialized or absent returns in dynamic typing contexts. It also avoids runtime surprises when a function unexpectedly fails to return a value.

It should further be noted that since Betty allows expression-statements as first-class citizens, functions can be executed solely for their side effects and have their values discarded.

```
print("Hello, world!"); # Valid, clearly intended for the side effect.
```