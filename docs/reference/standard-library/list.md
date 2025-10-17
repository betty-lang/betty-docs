# List

## append

| Property | Details |
|----------|---------|
| **Function** | `append(list, element)` |
| **Description** | Appends an element to a list. The first argument must be a list, and the second argument is the element to append to the list. Returns a new list with the appended element. |
| **Parameters** | `list` (List) – A list to which an element will be appended.<br>`element` (Any Type) – The element to append to the list. |
| **Return Type** | `List` – A new list containing the appended element. |
| **Errors** | If the first argument is not a list, an error will occur.<br>If the number of arguments is not exactly two, an error will occur. |
| **Example** | `append([1, 2, 3], 4)` → `[1, 2, 3, 4]` |

## range

| Property | Details |
|----------|---------|
| **Function** | `range(start, end)` |
| **Description** | Creates a range of numbers starting from start (inclusive) and ending at end (exclusive). Returns a list of numbers in the specified range. |
| **Parameters** | `start` (Number) – The starting number of the range.<br>`end` (Number) – The ending number of the range. |
| **Return Type** | `List` – A list of numbers from start to end (exclusive). |
| **Errors** | If the first or second argument is not a number, an error will occur.<br>If the number of arguments is not exactly two, an error will occur. |
| **Example** | `range(1, 5)` → `[1, 2, 3, 4]` |

## removeat

| Property | Details |
|----------|---------|
| **Function** | `removeat(list, index)` |
| **Description** | Removes the element at the specified index from the list. Returns a new list with the element at the given index removed. |
| **Parameters** | `list` (List) – The list from which to remove an element.<br>`index` (Number) – The index of the element to remove from the list. |
| **Return Type** | `List` – A new list with the specified element removed. |
| **Errors** | If the first argument is not a list, an error will occur.<br>If the second argument is not a number, an error will occur.<br>If the index is out of range, an error will occur. |
| **Example** | `removeat([1, 2, 3, 4], 2)` → `[1, 2, 4]` |

## remove

| Property | Details |
|----------|---------|
| **Function** | `remove(list, element)` |
| **Description** | Removes the first occurrence of element from the list. Returns a new list with the element removed. |
| **Parameters** | `list` (List) – The list from which to remove an element.<br>`element` (Any Type) – The element to remove from the list. |
| **Return Type** | `List` – A new list with the specified element removed. |
| **Errors** | If the first argument is not a list, an error will occur.<br>If the number of arguments is not exactly two, an error will occur. |
| **Example** | `remove([1, 2, 3, 4], 3)` → `[1, 2, 4]` |