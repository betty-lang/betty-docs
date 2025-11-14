# Control Flow

## `break` / `continue` / `return`

These control flow keywords are an integral part of the C-like programming
languages family (and many other families!).

- `break`: Breaks out of a loop construct, resuming execution at the first
statement after the loop's body.
- `continue`: Prematurely ends the current iteration of a loop, jumping to the
start of the next iteration.
- `return`: Returns control of the program to a function's caller. If this
statement is executed within a program's `main()` method, control is
returned to the operating system, effectively terminating the program.

### `break` Examples

```python
# Breaking out of a while loop
counter = 0;
while (true) {
    counter = counter + 1;
    if (counter == 5) {
        break;
    }
}
# counter = 5

# Breaking out of a for loop
counter = 0;
for (i = 0; i < 5; i = i + 1) {
    counter = counter + 1;
    if (counter == 3) {
        break;
    }
}
# counter = 3
```

### `continue` Examples

```python
# Continue in a while loop
counter = 0;
i = 0;
while (i < 5) {
    i = i + 1;
    if (i == 2) {
        continue;
    }
    counter = counter + 1;
}
# counter = 4 (skipped i == 2)

# Continue in a for loop
counter = 0;
for (i = 0; i < 5; i = i + 1) {
    if (i == 2) {
        continue;
    }
    counter = counter + 1;
}
# counter = 4

# Continue in nested loops
counter = 0;
i = 0;
while (i < 5) {
    i = i + 1;
    j = 0;
    while (j < 5) {
        j = j + 1;
        if (j == 3) {
            continue;  # Continues inner loop only
        }
        counter = counter + 1;
    }
}
# counter = 20
```

### `return` Examples

```python
# Return from a function
func add(a, b) {
    return a + b;
}

# Early return from a loop
func myfunc() {
    counter = 0;
    for (i = 0; i < 5; i++) {
        if (counter == 3) {
            return counter;
        }
        counter = counter + 1;
    }
}
# Returns 3

# Return from main terminates the program
func main() {
    for (i = 0; i < 5; i = i + 1) {
        if (i == 3) {
            return i;
        }
    }
    return 0;
}
```

## `if` / `elif` / `else`

Your standard issue, run-of-the-mill conditionals. `if` statements are used to execute a block of code, depending on whether a condition is true. An `if` statement can optionally be accompanied by a single or many `elif` statements, as well as an optional `else` statement at the end.

This is what the complete structure looks like:

```python
if (cond) {
    # if-body
}
elif (elsecond) {
    # elif-body
}
else {
    # else-body
}
```

### Basic Examples

```python
# Simple if statement
if (true) {
    return 42;
}

# If-else statement
if (false) {
    return 42;
}
else {
    return 0;
}

# If-elif statement
if (false) {
    return 42;
}
elif (true) {
    return 0;
}

# If-elif-else statement
if (false) {
    return 42;
}
elif (false) {
    return 0;
}
else {
    return 1;
}
```

### Single Statement Form

Single statements after conditionals don't require braces:

```python
if (true) return 42;

if (false) return 42;
else return 0;

if (false) return 42;
elif (true) return 0;
```

### Nested Conditionals

```python
if (false) {
    return 42;
}
elif (false) {
    return 0;
}
elif (true) {
    if (true) {
        return 1;
    }
}
else {
    return 2;
}
```

### If Expressions

Betty supports if expressions that return values and can be used in assignments:

```python
# Basic if expression
x = if 1 == 1 then 2 else 6;
# x = 2

# If expression with elif
x = if 1 == 2 then 2 elif 2 == 2 then 5 else 6;
# x = 5

# Multiple elif conditions
x = if 1 == 2 then 2 elif 2 == 3 then 5 elif 4 == 4 then 7 else 6;
# x = 7

# Nested if expressions
x = if 1 == 2 then 2 elif 2 == 2 then if 3 == 3 then 8 else 7 else 6;
# x = 8
```

## Ternary Operator

Betty supports the ternary conditional operator `? :` for concise conditional expressions:

```python
# Basic ternary
return true ? 1 : 0;  # Returns 1

# False condition
return false ? 1 : 2;  # Returns 2

# Nested ternary
return (true ? false : true) ? 1 : 2;  # Returns 2

# With arithmetic expressions
return (1 + 1 == 2) ? (3 * 2) : (4 / 2);  # Returns 6

# Within arithmetic expressions
return 10 + (false ? 100 : 200) * 2;  # Returns 410

# Complex nested ternary
return (5 > 3 ? 3 < 2 : 4 > 2) ? (7 == 7 ? 9 : 8) : (6 == 6 ? 10 : 11);
# Returns 10

# With function calls
return (2 == 2) ? add(4, 5) : multiply(3, 3);  # Returns 9
```

## Switch Statements and Expressions

Betty supports two forms of switch constructs: traditional switch statements for control flow, and switch expressions for value-returning pattern matching.

### Switch Expressions

Switch expressions use a concise syntax that evaluates to a value, making them ideal for assignments and inline usage. The syntax follows the pattern `value switch { pattern => result, ... }`.

#### Basic Syntax

```python
value switch {
    pattern1 => result1,
    pattern2 => result2,
    _ => defaultResult
}
```

The `_` (underscore) acts as a default case, matching any value that doesn't match previous patterns.

#### Basic Examples

```python
# Simple value matching
x = 2;
result = x switch {
    1 => "One",
    2 => "Two",
    3 => "Three",
    _ => "Other"
};
# result = "Two"

# Numeric results
grade = 'B';
points = grade switch {
    'A' => 4,
    'B' => 3,
    'C' => 2,
    'D' => 1,
    _ => 0
};
# points = 3

# String matching
day = "Monday";
type = day switch {
    "Monday" => "Weekday",
    "Tuesday" => "Weekday",
    "Saturday" => "Weekend",
    "Sunday" => "Weekend",
    _ => "Unknown"
};
# type = "Weekday"

# Boolean conditions
isActive = true;
status = isActive switch {
    true => "Active",
    false => "Inactive"
};
# status = "Active"
```

#### Switch After Function Calls

Switch expressions can be applied directly to the result of a function call:

```python
func getValue() { return 3; }

result = getValue() switch {
    1 => "One",
    2 => "Two",
    3 => "Three",
    _ => "Other"
};
# result = "Three"
```

#### Switch in Expressions

Switch expressions can be used anywhere an expression is expected:

```python
# In function arguments
func double(n) { return n * 2; }
x = 5;
result = double(x switch {
    5 => 10,
    10 => 20,
    _ => 0
});
# result = 20

# In indexer operations
arr = ["zero", "one", "two"];
x = 1;
result = arr[x switch {
    0 => 0,
    1 => 1,
    2 => 2,
    _ => 0
}];
# result = "one"

# In binary expressions
x = 2;
result = (x switch {
    1 => 10,
    2 => 20,
    _ => 0
}) + 5;
# result = 25
```

#### Nested Switch Expressions

Switch expressions can be nested within other switch expressions:

```python
x = 1;
y = 2;
result = x switch {
    1 => y switch {
        1 => "One-One",
        2 => "One-Two",
        _ => "One-Other"
    },
    2 => "Two",
    _ => "Other"
};
# result = "One-Two"
```

#### Switch with Lambda Functions

Switch expressions work seamlessly with lambda functions, making them powerful for functional programming patterns:

```python
# Returning different lambdas
mode = 2;
calculator = mode switch {
    1 => func(a, b) { return a + b; },
    2 => func(a, b) { return a * b; },
    3 => func(a, b) { return a - b; },
    _ => func(a, b) { return 0; }
};
result = calculator(7, 3);
# result = 21

# With closure capture
multiplier = 10;
type = "add";
operation = type switch {
    "add" => func(x) { return x + multiplier; },
    "multiply" => func(x) { return x * multiplier; },
    _ => func(x) { return x; }
};
result = operation(5);
# result = 15

# Returning list of lambdas
type = "math";
operations = type switch {
    "math" => [
        func(x) { return x + 1; },
        func(x) { return x * 2; }
    ],
    "string" => [
        func(x) { return x; }
    ],
    _ => []
};
result = operations[0](5) + operations[1](3);
# result = 12 (6 + 6)

# Matching on lambda equality
fn1 = func() { return 1; };
fn2 = func() { return 2; };
target = fn1;

result = target switch {
    fn1 => "First function",
    fn2 => "Second function",
    _ => "Unknown function"
};
# result = "First function"
```

### Switch Statements

Traditional C-style switch statements provide control flow with explicit fall-through behavior. Unlike many languages, Betty requires explicit `break` statements to prevent fall-through.

#### Basic Syntax

```python
switch (expression) {
    case value1:
        # statements
        break;
    case value2:
        # statements
        break;
    default:
        # statements
}
```

#### Basic Examples

```python
# Simple switch with breaks
x = 2;
switch (x) {
    case 1:
        return 10;
    case 2:
        return 20;
    case 3:
        return 30;
    default:
        return 40;
}
# Returns 20

# Switch with default case
x = 5;
switch (x) {
    case 1:
        return 10;
    case 2:
        return 20;
    default:
        return 40;
}
# Returns 40
```

#### Fall-Through Behavior

Without a `break` statement, execution continues into the next case:

```python
x = 1;
switch (x) {
    case 1:
        x = 2;
        # no break - falls through
    case 2:
        x = 3;
        # no break - falls through
    case 3:
        x = 4;
    default:
        x = 100;
}
# x = 100 (all cases executed)

# With break statements
x = 1;
switch (x) {
    case 1:
        x = 2;
        break;
    case 2:
        x = 3;
        break;
    case 3:
        x = 4;
        break;
    default:
        x = 100;
}
# x = 2 (only first case executed)
```

#### Scoped Case Bodies

Case bodies can be wrapped in braces to create a local scope:

```python
# Braced case with local scope
x = 1;
result = 0;
switch (x) {
    case 1: {
        temp = 100;
        result = temp;
        break;
    }
    case 2: {
        temp = 200;
        result = temp;
        break;
    }
}
# result = 100

# Mixed braced and unbraced cases
x = 2;
result = 0;
switch (x) {
    case 1:
        result = 10;
        break;
    case 2: {
        temp = 15;
        result = temp + 5;
        break;
    }
    case 3:
        result = 30;
        break;
}
# result = 20
```

#### Fall-Through with Shared Scope

When cases fall through without braces, they share the same scope:

```python
x = 1;
result = 0;
switch (x) {
    case 1:
        temp = 50;
        # no break - falls through
    case 2:
        result = temp + 10;  # Uses temp from case 1
        break;
}
# result = 60
```

!!!warning
    Switch statements in Betty do not automatically break after each case. You must explicitly use `break` to prevent fall-through to the next case. This behavior matches C-style switch statements and allows for intentional fall-through patterns.

!!!note
    Switch expressions are typically preferred over switch statements when you need to return a value, as they are more concise and expression-oriented. Use switch statements when you need complex control flow with multiple statements per case or when you want to leverage fall-through behavior.

## `for` / `foreach`

Although a language can do fine with just a while loop, for (and for-each) loops are a staple in C-like languages.

### For Loop

```python
for (initializer; condition; increment) {
    # body
}
```

#### Basic For Loop

```python
counter = 0;
for (i = 0; i < 5; i = i + 1) {
    counter = counter + 1;
}
# counter = 5
```

#### For Loop with Shorthand Increment

```python
counter = 0;
for (i = 0; i < 5; i++) {
    counter = counter + 1;
}
# counter = 5
```

#### Empty Components

Betty allows you to omit any or all components of a for loop:

```python
# Empty initializer
counter = 0;
for (; counter < 5; counter = counter + 1) {
    counter = counter + 1;
}

# Empty increment
counter = 0;
for (i = 0; i < 5; ) {
    counter = counter + 1;
    i = i + 1;
}

# Empty condition (creates infinite loop, use with break)
counter = 0;
for (i = 0; ; i = i + 1) {
    counter = counter + 1;
    if (counter == 5) {
        break;
    }
}

# All empty (infinite loop)
counter = 0;
for (; ; ) {
    counter = counter + 1;
    if (counter == 5) {
        break;
    }
}
```

!!!note
    In Betty, you may create a `for` loop without an initializer, condition or increment expression, or any other combination. This behavior closely aligns with how `for` loops work in many programming languages and was implemented in this manner for consistency purposes. Thus, `for (; ;)` can be used to create a non-terminating loop.

### For-Each Loop

The for-each loop uses the `in` keyword, expecting an iterable expression (like a list) after it.

```python
foreach (variableName in iterable) {
    # body
}
```

For-each loops can additionally be used to iterate through ranges and strings.

#### Range Iteration

```python
foreach (i in [1..5]) {
    println(i);     # Prints the numbers 1 to 4
}
```

#### String Iteration

```python
s = "Hello, World!";
foreach (c in s) {
    println(c);     # Prints each character in the string
}
```

## `while` / `do while`

While and do-while loops in Betty use standard syntax.

### While Loop

```python
while (condition) {
    # body
}
```

### Do-While Loop

```python
do {
    # body
} while (cond)
```

!!!note
    The body of any construct in Betty can either be a single statement or a compound statement (list of statements). In the case of singular statements, braces ( `{` `}` ) are not required. It is recommended that you use proper indentation and spacing to distinguish such statements from the statements succeeding them, ensuring code readability, should you choose to make use of this feature.