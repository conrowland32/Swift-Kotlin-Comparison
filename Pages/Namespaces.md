# Namespaces

## Swift

---

## Kotlin

Kotlin uses packages to define namespaces. Any source file can start with a package declaration:

```kotlin
package foo.bar
```

All the contents of the file (classes, functions, etc.) will be contained by the declared package:

```kotlin
package foo.bar

fun baz() {}

class Goo() {}
```

In the above example, both the function `baz` and the class `Goo` are members of `foo.bar`. Their full names will be `foo.bar.baz` and `foo.bar.Goo`.

If a package is not specified, the contents of the file will belong to a default package with no name.

Each file can contain its own `import` directives. We can import a single name:

```kotlin
import foo.Bar
```

We can also import all the contents of a scope:

```kotlin
import foo.*
```

The `import` keyword can be used to import classes, functions, properties, and enumerations.

[Back to Home](../README.md)
