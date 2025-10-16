## `func`

The `func` keyword is used to begin a function definition. Functions in Betty are
defined at the root level.

```py
func foo(param1, param2, ... , paramn)
{
    # body
}
```

Empty function definitions are valid in Betty, however duplicate definitions are
not. Function overloading is not supported at this moment.

Every Betty program requires a `main()` function as an entry point. If the
interpreter does not find one, an error will be raised. Intrinsic function
(standard library) function names are reserved and cannot be overridden. For a
comprehensive list of all built-in functions, refer to the [Standard Library](../standard-library/index.md).

!!!note
    Due to the dynamic nature of the Betty language, different code paths are
    allowed to return different data types. All functions, when in a code path where a return
    statement is omitted, implicitly return to the caller the unit-like value `None`, Betty’s
    “secret” type. Refer to the [`None`](../data-types/none.md) data type documentation for details.