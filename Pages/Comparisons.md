# Comparisons

## Swift

---

## Kotlin

In Kotlin, there are two different ways to check equality: structural equality checks, and referential equality checks.

### Structural Equality

Structural equality will check if the _values_ of the two items being compared are equivalent. Structural equality checks use the `==` operator (or the opposite, `!=`). Internally, the expression `a == b` is treated as:

```kotlin
a?.equals(b) ?: (b == null)
```

This means that if `a` is not `null`, it will call the `equals(Any?)` function. Otherwise, it will check if `b` is also equal to `null`.

### Referential Equality

Referential equality will check if the _references_ of the two items being compared are the same. Referential equality checks use the `===` operator (or the opposite, `!==`). The expression `a === b` will evaluate to true only if both `a` and `b` point to the same object or not, regardless of whether the objects are equal in value or not.

For primitive types, like number types, both `===` and `==` operate the same.

[Back to Home](../README.md)
