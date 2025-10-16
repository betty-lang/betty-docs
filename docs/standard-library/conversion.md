# Conversion

## tobool

| Property | Details |
|----------|---------|
| **Function** | `tobool(value)` |
| **Description** | Converts value to a boolean. Numbers, characters, and strings follow specific truthiness rules. |
| **Parameters** | `value` (number, char, string, or bool) – The value to convert. |
| **Return Type** | `bool` |
| **Conversion Rules** | **Numbers:** `0` → `false`, nonzero → `true`<br>**Chars:** Always `true`<br>**Strings:** `"true"` → `true`, `"false"` → `false`, empty → `false`, non-empty → `true`<br>**Booleans:** Returned as-is |
| **Errors** | Throws an exception if value is an unsupported type. |
| **Example** | `tobool(0)` → `false`<br>`tobool(42)` → `true`<br>`tobool('A')` → `true`<br>`tobool("")` → `false`<br>`tobool("true")` → `true`<br>`tobool("false")` → `false` |

## tochar

| Property | Details |
|----------|---------|
| **Function** | `tochar(value)` |
| **Description** | Converts value to a character if possible. Different types follow specific conversion rules. |
| **Parameters** | `value` (number, char, string, or bool) – The value to convert. |
| **Return Type** | `char` |
| **Conversion Rules** | **Numbers:** Cast to char if within valid range.<br>**Chars:** Returned as-is.<br>**Strings:** Must be exactly one character long.<br>**Booleans:** `true` → `'T'`, `false` → `'F'` |
| **Errors** | Throws an exception if value is an unsupported type, a number outside the valid character range, or a string longer than one character. |
| **Example** | `tochar(65)` → `'A'`<br>`tochar('Z')` → `'Z'`<br>`tochar("B")` → `'B'`<br>`tochar(true)` → `'T'`<br>`tochar(false)` → `'F'` |

## tolist

| Property | Details |
|----------|---------|
| **Function** | `tolist(value)` |
| **Description** | Converts a string into a list of characters. Each character in the string becomes an individual element in the list. |
| **Parameters** | `value` (string) – The string to convert into a list of characters. |
| **Return Type** | `list` (of char) |
| **Errors** | Throws an exception if value is not a string. |
| **Example** | `tolist("abc")` → `['a', 'b', 'c']`<br>`tolist("7")` → `['7']` |

## tonum

| Property | Details |
|----------|---------|
| **Function** | `tonum(value)` |
| **Description** | Converts a value into a number. Strings are parsed as numbers, booleans convert to 1 (true) or 0 (false), and characters are converted to their numeric values. |
| **Parameters** | `value` (char, string, boolean, or number) – The value to convert into a number. |
| **Return Type** | `number` |
| **Errors** | Throws an exception if value is a string that cannot be converted to a number or if value is of an unsupported type. |
| **Example** | `tonum('5')` → `5`<br>`tonum("42.3")` → `42.3`<br>`tonum(true)` → `1`<br>`tonum(false)` → `0` |

## tostr

| Property | Details |
|----------|---------|
| **Function** | `tostr(value)` |
| **Description** | Converts a value into a string representation. |
| **Parameters** | `value` (any type) – The value to convert into a string. |
| **Return Type** | `string` |
| **Errors** | None (all values have a string representation). |
| **Example** | `tostr(42)` → `"42"`<br>`tostr(true)` → `"true"`<br>`tostr('A')` → `"A"` |