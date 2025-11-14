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

## Local Named Functions

While the statement "functions are defined at the root level" applies to globally accessible functions, Betty also supports defining named functions locally within other functions and blocks. These local named functions use the same `func name() { }` syntax as global functions but have limited scope visibility.

### Basic Local Functions

Local named functions can be defined inside any function or block:

```py
func main() {
    func greet() { return "Hello"; }
    return greet(); # Returns "Hello"
}
```

### Local Functions with Parameters

Like global functions, local functions can accept parameters:

```py
func main() {
    func add(a, b) { return a + b; }
    return add(2, 3); # Returns 5
}
```

### Closures (Read-Only)

Local named functions can capture variables from their enclosing scope, creating closures. However, closures in Betty are currently **read-only** - captured variables can be read but not modified:

```py
func main() {
    x = 10;
    func multiply(y) { return x * y; }
    return multiply(3); # Returns 30
}
```

```py
func main() {
    a = 5;
    b = 10;
    func compute() {
        c = 15;
        return a + b + c; # Can read a and b from outer scope
    }
    return compute(); # Returns 30
}
```

!!!warning
    Closures in Betty are read-only. Local functions can read variables from enclosing scopes but cannot modify them. Attempting to assign to a captured variable will create a new local variable instead of modifying the outer one.

### Recursive Local Functions

Local named functions can call themselves recursively:

```py
func main() {
    func fact(n) {
        if (n <= 1) { return 1; }
        return n * fact(n - 1);
    }
    return fact(5); # Returns 120
}
```

### Nested Local Functions

Local functions can be nested within other local functions:

```py
func main() {
    func outer() {
        func inner() { return 42; }
        return inner();
    }
    return outer(); # Returns 42
}
```

### Function Shadowing

Local functions can shadow global functions or other local functions in outer scopes:

```py
# Shadowing global functions
func getValue() { return 100; }
func main() {
    func getValue() { return 200; }
    return getValue(); # Returns 200
}
```

```py
# Shadowing in nested blocks
func main() {
    func getValue() { return 10; }
    x = getValue();
    {
        func getValue() { return 20; }
        x = x + getValue();
    }
    x = x + getValue();
    return x; # Returns 40 (10 + 20 + 10)
}
```

When a shadowed function goes out of scope, the outer function becomes accessible again:

```py
func getValue() { return 100; }
func main() {
    outer = getValue();
    {
        func getValue() { return 200; }
        inner = getValue();
    }
    after = getValue();
    return outer + after; # Returns 200 (100 + 100)
}
```

### Block-Level Scoping

Local functions defined in different blocks can have the same name without conflict:

```py
func main() {
    result = 0;
    {
        func addOne() { return 1; }
        result = result + addOne();
    }
    {
        func addOne() { return 10; }
        result = result + addOne();
    }
    return result; # Returns 11 (0 + 1 + 10)
}
```

### Returning Local Functions

Local functions can return other local functions, creating closure factories:

```py
func main() {
    func makeAdder(x) {
        func adder(y) { return x + y; }
        return adder;
    }
    add5 = makeAdder(5);
    return add5(10); # Returns 15
}
```

Each returned function captures its own copy of the closure variables:

```py
func main() {
    func makeMultiplier(factor) {
        func multiply(n) { return n * factor; }
        return multiply;
    }
    double = makeMultiplier(2);
    triple = makeMultiplier(3);
    return double(5) + triple(5); # Returns 25 ((5*2) + (5*3))
}
```

### Assigning to Variables

Local named functions can be assigned to variables, just like lambdas:

```py
func main() {
    func greet() { return "Hello"; }
    fn = greet;
    return fn(); # Returns "Hello"
}
```

### Calling Between Local Functions

Local functions can call other local functions defined in the same scope:

```py
func main() {
    func add(a, b) { return a + b; }
    func addAndDouble(a, b) { return add(a, b) * 2; }
    return addAndDouble(3, 4); # Returns 14
}
```

### Passing as Arguments

Local functions can be passed as arguments to other functions:

```py
func main() {
    func apply(fn, value) { return fn(value); }
    func square(x) { return x * x; }
    return apply(square, 4); # Returns 16
}
```

### Mixed with Lambdas

Local named functions and lambda expressions can be used together seamlessly:

```py
func main() {
    func named(x) { return x + 1; }
    lambda = func(x) { return x * 2; };
    return named(5) + lambda(5); # Returns 16 (6 + 10)
}
```

!!!note
    The primary difference between local named functions (`func name() { }`) and lambda expressions (`name = func() { }`) is syntactic. Both create first-class function values that can be passed around, assigned to variables, and used in closures. Choose local named functions for clarity when defining helper functions within a scope, and lambdas when you need to create function values inline or store them in data structures.