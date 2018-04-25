# Errors and Exception Handling

## Swift

---

## Kotlin

Kotlin uses Exceptions to handle thrown errors. All exception classes are descendants of the `Throwable` class. Each exception will always include a message, a stack trace, and an optional clause.

Exceptions are thrown using the `throw` keyword:

```kotlin
throw MyException("Exception thrown.");
```

Exceptions can also be used in try-catch blocks:

```kotlin
try {
    //application code
} catch (ex: MyException) {
    //exception handler
}
```

It is important to note that all exceptions in Kotlin are unchecked; there are no checked exceptions.

In Kotlin, `throw` is an expression of type `Nothing`. This type does not hold values, but can be used to mark locations in code that can never be reached. For example, `Nothing` can be used to indicate that a desired function is never intended to return:

```kotlin
fun fail(message: String): Nothing {
    throw IllegalArgumentException(message)
}
```

When this function is called, the compiler knows that the execution will not continue after it is called. Therefore, it can be used as a logical breakpoint:

```kotlin
val s = person.name ?: fail("No name")
println(s)   //if the code reaches this point, we know 's' must be initialized
```

[Back to Home](../README.md)
