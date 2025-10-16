# Example 3: Comments and Integer Division

Illustrates the use of integer division shorthand and how to include comments.

```python
func divisionExample()
{
    x = 10;
    y = 20;
    y //= 2;    # Integer division shorthand
    print(y);   # Outputs 10

    # This is a comment explaining that the next line prints the value of x
    
    print(x);   # Outputs 10
}

func main()
{
    divisionExample();
}
```