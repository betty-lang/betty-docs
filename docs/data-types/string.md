# String

Strings in Betty are enclosed between a pair of double quotes ( `"` ). They are interned using a string lookup table so they can be lightweight&mdash;in terms of memory overhead and allocations (on the stack vs. the heap), as well as be accessed very fast in ideal usage scenarios.

```python
"Hello, World!";
```

In an addition operation, if either operand is a `string`, then the result is concatenated and returned as a `string`. This has been implemented to match the expected behavior in several programming languages.

```python
"Hi " + 5; # Returns "Hi 5"
```

Furthermore, in addition to equality and inequality operations, strings allow comparisons like `>` and `<`, based on lexicographical order. This behavior may not always make intuitive sense to a newer programmer, nonetheless it is supported in plenty of programming languages. In the back-end, C#'s `CompareTo` standard library function (akin to `strcmp` in C) is utilized.

```python
"apple" < "banana"; # Returns `true`, since 'a' is less than 'b'
```

Compound (shorthand assignment) is supported in strings only through the addition ( `+` ) operator.

## Escape sequences

| Sequence | Description      |
|----------|------------------|
| `\n`     | Newline          |
| `\t`     | Tab              |
| `\"`     | Double quote     |
| `\'`     | Single quote     |
| `\\`     | Backslash        |
| `\0`     | Null character   |

!!!note
    Character literals also support the aforementioned sequences.