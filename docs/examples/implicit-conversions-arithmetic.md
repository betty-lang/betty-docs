# Example 2: Implicit Conversions and Arithmetic

Discover how Betty handles automatic type conversions and performs arithmetic operations across different data types.

```python
func charArithmetic()
{
    charValue = 'a';
    charValue += 1;     # Implicitly converts 'a' to its ASCII value, then increments
    print(charValue);   # Outputs the number corresponding to 'b' in ASCII
    numberValue = 10;
    numberValue += '3'; # '3' is implicitly converted to its numeric ASCII value before addition
    print(numberValue); # Outputs the result of the addition
}
```