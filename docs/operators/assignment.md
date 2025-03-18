# Assignment Operators

| Operator  | Description        | Example        | Equivalent To |
|-----------|--------------------|---------------|--------------|
| `=`       | Assign value       | `x = 5`       | `x = 5`      |

## Compound assignment

| Operator  | Description                | Example        | Equivalent To  |
|-----------|----------------------------|---------------|---------------|
| `+=`      | Add and assign             | `x += 3`      | `x = x + 3`   |
| `-=`      | Subtract and assign        | `x -= 2`      | `x = x - 2`   |
| `*=`      | Multiply and assign        | `x *= 4`      | `x = x * 4`   |
| `/=`      | Divide and assign          | `x /= 2`      | `x = x / 2`   |
| `%=`      | Modulus and assign         | `x %= 3`      | `x = x % 3`   |
| `^=`     | Exponentiate and assign    | `x ^= 2`     | `x = x ^ 2`  |
| `//=`     | Floor divide and assign    | `x //= 2`     | `x = x // 2`  |

## Prefix & postfix increment/decrement

| Operator  | Type    | Description                       | Example           | Result         |
|-----------|---------|-----------------------------------|-------------------|----------------|
| `++x`     | Prefix  | Increments `x` before evaluation  | `x = 5; y = ++x;` | `x = 6, y = 6` |
| `x++`     | Postfix | Increments `x` after evaluation   | `x = 5; y = x++;` | `x = 6, y = 5` |
| `--x`     | Prefix  | Decrements `x` before evaluation  | `x = 5; y = --x;` | `x = 4, y = 4` |
| `x--`     | Postfix | Decrements `x` after evaluation   | `x = 5; y = x--;` | `x = 4, y = 5` |
