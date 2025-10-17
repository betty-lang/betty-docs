# Math

## abs

| Property | Details |
|----------|---------|
| **Function** | `abs(number)` |
| **Description** | Returns the absolute value of the given number. |
| **Parameters** | `number` (Number) – The number for which to return the absolute value. |
| **Return Type** | `Number` – The absolute value of the provided number. |
| **Errors** | If the argument is not a number, an error will occur.<br>If the number of arguments is not exactly one, an error will occur. |
| **Example** | `abs(-5)` → `5`<br>`abs(3)` → `3` |

## ceil

| Property | Details |
|----------|---------|
| **Function** | `ceil(number)` |
| **Description** | Returns the smallest integer greater than or equal to the given number. |
| **Parameters** | `number` (Number) – The number for which to return the ceiling value. |
| **Return Type** | `Number` – The smallest integer greater than or equal to the provided number. |
| **Errors** | If the argument is not a number, an error will occur.<br>If the number of arguments is not exactly one, an error will occur. |
| **Example** | `ceil(4.2)` → `5`<br>`ceil(-1.7)` → `-1` |

## cos

| Property | Details |
|----------|---------|
| **Function** | `cos(number)` |
| **Description** | Returns the cosine of the given number (interpreted as an angle in radians). |
| **Parameters** | `number` (Number) – The angle in radians for which to compute the cosine value. |
| **Return Type** | `Number` – The cosine of the provided angle. |
| **Errors** | If the argument is not a number, an error will occur.<br>If the number of arguments is not exactly one, an error will occur. |
| **Example** | `cos(0)` → `1` |

## floor

| Property | Details |
|----------|---------|
| **Function** | `floor(x)` |
| **Description** | Returns the largest integer less than or equal to x. |
| **Parameters** | `x` (Number) – The number to round down. |
| **Return Type** | `Number` |
| **Errors** | Throws an error if x is not a number. |
| **Example** | `floor(3.7)` → `3`<br>`floor(-2.3)` → `-3` |

## pow

| Property | Details |
|----------|---------|
| **Function** | `pow(base, exponent)` |
| **Description** | Returns base raised to the power of exponent. |
| **Parameters** | `base` (Number) – The base value.<br>`exponent` (Number) – The exponent value. |
| **Return Type** | `Number` |
| **Errors** | Throws an error if arguments are not numbers. |
| **Example** | `pow(2, 3)` → `8`<br>`pow(5, 0.5)` → `2.236` |

## sin

| Property | Details |
|----------|---------|
| **Function** | `sin(angle)` |
| **Description** | Returns the sine of angle, where angle is given in radians. |
| **Parameters** | `angle` (Number) – The angle in radians. |
| **Return Type** | `Number` |
| **Errors** | Throws an error if the argument is not a number. |
| **Example** | `sin(0)` → `0`<br>`sin(3.14159 / 2)` → `1` |

## sqrt

| Property | Details |
|----------|---------|
| **Function** | `sqrt(number)` |
| **Description** | Returns the square root of number. |
| **Parameters** | `number` (Number) – The value to find the square root of. |
| **Return Type** | `Number` |
| **Errors** | Throws an error if the argument is not a number. |
| **Example** | `sqrt(9)` → `3`<br>`sqrt(2)` → `1.41421` |

## tan

| Property | Details |
|----------|---------|
| **Function** | `tan(number)` |
| **Description** | Returns the tangent of number, where number is in radians. |
| **Parameters** | `number` (Number) – The angle in radians. |
| **Return Type** | `Number` |
| **Errors** | Throws an error if the argument is not a number. |
| **Example** | `tan(0)` → `0`<br>`tan(pi / 4)` → `1` |