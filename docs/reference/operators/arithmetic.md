# Arithmetic Operators

| Operator | Description     | Example     |
|----------|-----------------|-------------|
| `+`      | Addition        | `1 + 2` → `3` |
| `-`      | Subtraction     | `5 - 3` → `2` |
| `*`      | Multiplication  | `4 * 2` → `8` |
| `/`      | Division        | `8 / 2` → `4` |
| `%`      | Modulus         | `10 % 3` → `1` |
| `^`     | Exponentiation  | `2 ^ 3` → `8` |
| `//`     | Floor Division  | `7 // 2` → `3` |

## Addition overloads

### String concatenation

The addition operator has been overloaded to support string concatenation. Therefore, syntax such as `"Hello " + "World"` is possible in Betty.

!!!note
    String concatenation is also supported through an appropriately-named `concat()` built-in language function, as well as the `print()` function itself. Further examples of **string manipulation** can be found in the intrinsic functions documentation.

### List-operand addition

If either operand of an addition operation is a `list`, the interpreter will append the other operand to it&mdash;either at the beginning or the end, depending on the operand order. If both operands are lists, the second list will be appended to the end of the first.

Since lists are reference types in Betty, this operation modifies the original list rather than creating a new one.

Cases:

- `list + element` would append `element` to the end of `list`.
- `element + list` would prepend `element` to the beginning of `list`.
- `list1 + list2` would append `list2` to `list1`, modifying `list1`.

Example:

```
a = "hello";
b = [1, 2];
return b + a; # Will append the string to the end of `b`, i.e. [1, 2, "hello"]
```

## Implicit conversions

For the sake of convenience and flexibility, Betty will handle some common scenarios implicitly, as far as the expected outcome of "adding" different data types is concerned. For those who prefer boldness and completeness over simplicity&mdash;although type hinting is not a feature&mdash;the language constructs do
allow you to explicitly specify most conversion operations.

### Character arithmetic

In Betty, characters are implicitly converted to their ASCII values when used in arithmetic operations. This allows direct manipulation of characters as numeric values.

```
charValue = 'a';
charValue += 1;         # Implicitly converts 'a' to its ASCII value, then increments
print(charValue);       # Outputs the number corresponding to 'b' in ASCII
numberValue = 10;
numberValue += '3';     # '3' is implicitly converted to its numeric ASCII value before addition
print(numberValue);     # Outputs the result of the addition
```

!!!note
    As types in Betty are, for the most part, **not strictly enforced**, the interpreter will automatically handle conversions like these to reduce friction and boilerplate code.

!!!warning
    In order to avoid confusion and ensure clarity, an explicit conversion back to `char` would be needed in order to print the character representations in the example.