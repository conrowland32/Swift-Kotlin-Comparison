# Null/Nil References

## Swift

---

## Kotlin

### Creating Nullables

Like many new languages, Kotlin introduces a way to reduce the possibility of null references in code. Kotlin does this through _nullable_ types. In Kotlin, the type system distinguishes between references that are allowed to hold `null` (nullable references) and those that can not.

For example, a normal variable of type `String` is not allowed to hold `null`:

```kotlin
var a: String = "abc"
a = null   //compile error
```

To allow a variable to hold null, you must declare it as nullable using a `?` after the type:

```kotlin
var b: String? = "abc"
b = null   //okay
```

Since the variable `a` is defined as non-nullable, it is guaranteed to never hold null. We can therefore safely access a field or method on it:

```kotlin
val l = a.length
```

However, if we want to access the same field or method on `b`, which _is_ nullable, it is not safe because `b` could potentially be `null`:

```kotlin
val l = b.length   //compile error: 'b' can be null
```

### Accessing Nullables

Even though some variables are defined as nullable, we still want to access fields and properties on those variables. In order to do this, we must first check that a nullable type is not currently holding a null reference.

#### Option 1: Explicit Checks

The first way to do this is to explicitly check that the variable is not null:

```kotlin
if (b != null) {
    val l = b.length
} else {
    print("Error: b is null")
}
```

Once you check that the variable is not null, the compiler will track the check and allow you to access the variable. Explicitly checking for `null` using this method is good for simple applications, but can become tedious in larger applications because the check must be performed every time the variable could have changed.

#### Option 2: Safe Calls

The second way to access a nullable is through the _safe call_ operator, `?.`:

```kotlin
b?.length
```

This statement returns `b.length` is `b` is not null. Otherwise, it returns `null`.

Safe calls are useful because they can be used in chains:

```kotlin
bob?.department?.head?.name
```

The chain will return `null` if any of the references are null.

Safe calls can also be used with the _Elvis Operator_, `?:`. The Elvis operator behaves like a ternary operator for nullables. It says, "If the statement is not null, use it. Otherwise, use some other non-null value." The same ternary statement, with and without the Elvis operator:

```kotlin
val l: Int = if (b != null) b.length else -1   //without Elvis operator

val l: Int = b?.length ?: -1   //with Elvis operator
```

We can also use the Elvis operator to do more advanced actions, like `return` or `throw` based on a nullable:

```kotlin
fun foo(node: Node): String? {
    val parent = node.getParent() ?: return null
    val name = node.getName() ?: throw IllegalArgumentException("name expected")
}
```

#### Option 3: Not-null Assertion

The third option, the not-null assertion operator `!!` allows you to explicitly access a nullable. If the variable is `null`, the operation will throw a null pointer exception:

```kotlin
val l = b!!.length
```

The not-null assertion is the only way to throw a null pointer exception in Kotlin, and should therefore be used rarely, if ever.

[Back to Home](../README.md)
