# Number

Betty uses a universal `number` data type to represent both integers and real numbers. Internally, all numeric values are stored as `double` for ease of handling. The language does, in fact, offer ways to work with strictly integer values, at least on the surface level, should one wish to do so.

For instance, there are built-in math functions baked into the language for both `floor()` and `ceil()`. Additionally, there exists an integer division operator ( `//` ), which performs normal double division then floors the result, as is the case in several programming languages (e.g. Python, Ruby).

```
12
0.5
0.002
-3
```

Under the hood, Betty leverages C#'s and, by extension, .NET's own `double` primitive value type, which means edge cases such as `infinity` and `NaN` are handled by the underlying framework implementation at the binary level.