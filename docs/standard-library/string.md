# String

## concat

| Property | Details |
|----------|---------|
| **Function** | `concat(value1, value2, ...)` |
| **Description** | Concatenates all given values into a single string. |
| **Parameters** | Any number of values of any type. Each value is converted to a string before concatenation. |
| **Return Type** | `String` |
| **Errors** | None. All values are implicitly converted to strings. |
| **Example** | `concat("Hello", " ", "World!")` → `"Hello World!"`<br>`concat(42, " is the answer")` → `"42 is the answer"` |

## len

| Property | Details |
|----------|---------|
| **Function** | `len(value)` |
| **Description** | Returns the length of a string or list. |
| **Parameters** | `value` – A string or list. |
| **Return Type** | `Number` – The length of the string or list. |
| **Errors** | Throws an error if the argument is not a string or list. |
| **Example** | `len("Hello")` → `5`<br>`len([1, 2, 3, 4])` → `4` |