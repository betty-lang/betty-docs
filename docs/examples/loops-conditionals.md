# Example 6: Loops and Conditionals

Showcases loops (`while`, `for`) and conditional (`if-else`) statements.

```python
func loopExamples()
{
    # While loop example
    i = 0;
    while (i < 5)
    {
        print(i);
        i++;
    }
    
    # For loop example
    for (j = 0; j < 5; j++)
    {
        print(j);
    }

    # If-else example
    if (i == 5)
    {
        print("Loop completed with while");
    }
    else
    {
        print("Unexpected value");
    }
}

func main()
{
    loopExamples();
}
```