# Char

Character literals are encased between a pair of single quotes ( `'` ). Empty character literals are not allowed in Betty programs. A character literal may not consist of more than one character, save for escape sequences&mdash;which essentially are single characters.

```python
x = 'b';    # Valid
x = '\n';   # Valid, escape sequence
x = '';     # Will throw, empty character literal
x = 'ab';   # Will throw, multi-character literal
x = ';      # Will throw, unterminated character literal
```

!!!note
    Some operations between numbers and characters (character arithmetic) are handled implicitly by the interpreter, to an extent. Refer to the operator documentation syntax for further details, as well as to explore options for handling such operations explicitly.