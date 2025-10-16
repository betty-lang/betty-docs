## `break` / `continue` / `return`

These control flow keywords are an integral part of the C-like programming
languages family (and many other families!).

- `break`: Breaks out of a loop construct, resuming execution at the first
statement after the loop’s body.
- `continue`: Prematurely ends the current iteration of a loop, jumping to the
start of the next iteration.
- `return`: Returns control of the program to a function’s caller. If this
statement is executed within a program’s `main()` method, control is
returned to the operating system, effectively terminating the program.

## `if` / `elif` / `else`

Your standard issue, run-of-the-mill conditionals. `if` statements are used to execute a block of code, depending on whether a condition is true. An `if` statement can optionally be accompanied by a single or many `elif` statements, as well as an optional `else` statement at the end.

This is what the complete structure looks like.

```py
if (cond)
{
    # if-body
}
elif (elsecond)
{
    # elif-body
}
else
{
    # else-body
}
```

## `for` / `foreach`

Although a language can do fine with just a while loop, for (and for-each) loops are a staple in C-like languages.

```py
for (initializer; condition; increment)
{
    # body
}
```

!!!note
    In Betty, you may create a `for` loop without an initializer, condition or increment expression, or any other combination. This behavior closely aligns with how `for` loops work in many programming languages and was implemented in this manner for consistency purposes. Thus, `for (; ;)` can be used to create a non-terminating loop.

The for-each loop uses the `in` keyword, expecting an iterable expression (like a list) after it.

```py
foreach (variableName in iterable)
{
    # body
}
```

For-each loops can additionally be used to iterate through ranges and strings.

Range iteration:
```py
foreach (i in [1..5])
{
    println(i);     # Prints the numbers 1 to 4
}
```

String iteration:
```py
s = "Hello, World!";
foreach (c in s)
{
    println(c);     # Prints each character in the string
}
```

## `while` / `do while`

While and do-while loops in Betty use standard syntax.

While loop:
```py
while (condition)
{
    # body
}
```

Do-while loop:
```py
do
{
    # body
} while (cond)
```

!!!note
    The body of any construct in Betty can either be a single statement or a compound statement (list of statements). In the case of singular statements, braces ( `{` `}` ) are not required. It is recommended that you use proper indentation and spacing to distinguish such statements from the statements succeeding them, ensuring code readability, should you choose to make use of this feature.