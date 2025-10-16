# Example 5: Control Flow and Recursion

A simple demonstration of recursion and the `if` control structure to calculate a factorial.

```python
func factorial(n)
{
    if (n == 1)
    {
        return 1;
    }
    else
    {
        return n * factorial(n - 1);    # Recursive call
    }
}

func main()
{
    result = factorial(5);
    print(result);                      # Should print 120, the factorial of 5
}
```