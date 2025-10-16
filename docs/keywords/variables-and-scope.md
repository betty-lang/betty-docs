## `global`

The `global` keyword is used to declare a global, program-wide variable. Global
variable declarations in Betty are top-level statements. Global variables cannot
be assigned to on declaration and cannot be shadowed. They can be declared
anywhere in the code’s root level, nonetheless it is encouraged to declare them
at the start of the program.

The decision to include global variables in a programming language can
admittedly be rather controversial, as such a design strays away from pure and
clean programming practices. Care should be exercised, as careless usage of
globals can be headache-inducing.

That being said, Betty’s syntax for global variables is very straightforward.

```python
global x;           # Declares ‘x’ as a global variable

func side_effect()
{
    x = 10;
}

func main()
{
    x = 2;
    side_effect();
    print(x);       # Will print ‘10’
}
```