# List

Lists are currently the sole data structure of the Betty language, its bread and butter so to speak. Aided by the language's dynamic design, lists are very versatile in terms of their usage and what they can accomplish.

Betty allows lists containing multiple data types, even different (nested) lists. Despite the lack of other data structures in the language, the flexibility achieved through this alone enables for "custom" record-like structures, even&mdash;admittedly lesser-performing&mdash; maps.

!!!note
    In the code examples section of the documentation, you can find a partial, preliminary attempt at **bootstrapping** (self-hosting) the Betty interpreter, showcasing the language's potential. Naturally, although such an implementation would result in less-than-ideal execution times, it is nonetheless a rather fun theoretical endeavor to take on.

Betty is primarily a prototyping language, that much is certain. Be that as it may, the presence of lists&mdash;along with some useful standard library functions, can assist the user in coding solutions to a multitude of problems. That was a major consideration in the way lists are implemented.

One of the goals in the development process was to provide the programmer with ways to create something more meaningful than your typical "Hello World," even at the cost of potential performance (the unavoidable tree-walk interpreter baggage). Whether they decide to "get their hands dirty" is ultimately left up to the user.

```
x = [1, 2, 3, 4];
x = [1..5];             # Same declaration with range syntax
x = [[1, 2], [3, 4]];   # Nested lists
```

## String indexing

Betty supports indexing strings and accessing them as character lists out-of-the-box, in alignment with the default behavior in various programming languages.

```
print("hello"[1]); # Will print `e`
```