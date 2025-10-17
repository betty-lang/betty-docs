# Variables

## Variable Assignment

Variables in Betty are dynamically typed and do not require explicit type declarations. A variable is created simply by assigning a value to it:

```python
x = 5;              # Number variable
name = "Alice";     # String variable
flag = true;        # Boolean variable
mylist = [1, 2, 3]; # List variable
```

### Assignment with Expressions

Variables can be assigned the result of any expression:

```python
x = 2 + 3;          # x = 5
y = x * 2;          # y = 10
z = foo();          # z = return value of foo()
```

### Chain Assignment

Multiple variables can be assigned the same value in a single statement:

```python
x = y = 5;          # Both x and y are assigned 5
a = b = c = 10;     # Multiple chain assignment
```

---

## Global Variables

The `global` keyword is used to declare a global, program-wide variable. Global
variable declarations in Betty are top-level statements. Global variables cannot
be assigned to on declaration. They can be declared anywhere in the code's root 
level, nonetheless it is encouraged to declare them at the start of the program.

The decision to include global variables in a programming language can
admittedly be rather controversial, as such a design strays away from pure and
clean programming practices. Care should be exercised, as careless usage of
globals can be headache-inducing.

That being said, Betty's syntax for global variables is very straightforward.

```python
global x;           # Declares 'x' as a global variable

func side_effect()
{
    x = 10;
}

func main()
{
    x = 2;
    side_effect();
    print(x);       # Will print '10'
}
```

## Scope and Shadowing

Global variables can be shadowed by function parameters. When a function parameter has the same name as a global variable, the parameter takes precedence within that function's scope, leaving the global variable unchanged:

```python
global x;

func foo(x) {
    x = 4;          # Modifies the parameter, not the global
}

func main() {
    x = 5;          # Sets global x to 5
    foo(3);         # Parameter x shadows global x
    print(x);       # Prints '5' - global x is unchanged
}
```

## Access Across Functions

Global variables can be accessed and modified by any function in the program:

```python
global x;

func main() {
    x = 5;          # Sets global x to 5
    other();        # Calls other(), which modifies x
    print(x);       # Prints '3' - x was modified by other()
}

func other() {
    x = 3;          # Modifies the global x
}
```