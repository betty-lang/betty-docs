# Functions

The `func` keyword is used to begin a function definition. Functions in Betty are
defined at the root level.

```py
func foo(param1, param2, ... , paramn)
{
    # body
}
```

Empty function definitions are valid in Betty, however duplicate definitions are
not. Function overloading is not supported at this moment.

Every Betty program requires a `main()` function as an entry point. If the
interpreter does not find one, an error will be raised. Intrinsic function
(standard library) function names are reserved and cannot be overridden. For a
comprehensive list of all built-in functions, refer to the [Standard Library](../standard-library/index.md).

!!!note
    Due to the dynamic nature of the Betty language, different code paths are
    allowed to return different data types. All functions, when in a code path where a return
    statement is omitted, implicitly return to the caller the unit-like value `None`, Betty's
    "secret" type. Refer to the [`None`](../data-types/none.md) data type documentation for details.

## Recursion

Functions in Betty support recursion, allowing a function to call itself:

```py
func fact(n) {
    if (n <= 1) { return 1; }
    return n * fact(n - 1);
}

func main() {
    return fact(5); # Returns 120
}
```

## Lambdas

Lambda functions (also called function expressions or anonymous functions) can be created using the `func` keyword without a name. These can be assigned to variables, passed as arguments, stored in data structures, or called immediately.

### Basic Lambda Assignment

```py
func main() {
    greet = func() { return "Hello"; };
    return greet(); # Returns "Hello"
}
```

### Lambdas with Parameters

Lambda functions can accept parameters just like regular functions:

```py
func main() {
    add = func(a, b) { return a + b; };
    return add(2, 3); # Returns 5
}
```

### Closures

Lambda functions can capture variables from their surrounding scope, creating closures:

```py
func main() {
    x = 10;
    multiply = func(y) { return x * y; };
    return multiply(3); # Returns 30
}
```

### Recursive Lambdas

Lambda functions can be recursive by referencing their assigned variable name:

```py
func main() {
    fact = func(n) {
        if (n <= 1) { return 1; }
        return n * fact(n - 1);
    };
    return fact(5); # Returns 120
}
```

### Nested Lambdas

Lambda functions can be nested within other lambdas:

```py
func main() {
    outer = func() {
        inner = func() { return 42; };
        return inner();
    };
    return outer(); # Returns 42
}
```

### Higher-Order Functions

Lambda functions can be passed as arguments to other functions:

```py
func main() {
    apply = func(fn, value) { return fn(value); };
    square = func(x) { return x * x; };
    return apply(square, 4); # Returns 16
}
```

### Immediately Invoked Lambda Expressions

Lambda functions can be called immediately upon creation:

```py
func main() {
    return (func() { return 42; })(); # Returns 42
}
```

### Lambdas in Data Structures

Function expressions can be stored in lists and other data structures:

```py
func main() {
    funcs = [
        func(x) { return x + 1; },
        func(x) { return x * 2; }
    ];
    
    result1 = funcs[0](3); # Returns 4
    result2 = funcs[1](3); # Returns 6
    
    return result1 + result2; # Returns 10
}
```

### Function Reference Equality

Function references are compared by identity. Two variables pointing to the same function are equal, but two separately defined functions (even with identical implementations) are not:

```py
func main() {
    greet1 = func() { return "Hello"; };
    greet2 = greet1; # Same reference
    greet3 = func() { return "Hello"; }; # Different function
    
    greet1 == greet2; # true - same reference
    greet1 == greet3; # false - different functions
}
```