# Example 1: Functions and Unary Operations

Demonstrates how to define a function and use post-increment and pre-increment operations.

```python
func increment()
{
    count = 0;
    count = count++ + ++count;  # Post-increment and pre-increment
    print(count);               # Should output 2, demonstrating how increment operations work
}

func main()
{
    increment();
}
```