# Reflection

## Swift

---

## Kotlin

Kotlin includes several ways to reflect on both functions and properties.

### Class References

Kotlin allows you to retrieve the runtime reference to a Kotlin class using the _class literal_ syntax:

```kotlin
val c = MyClass::class
```

Kotlin also includes the `is` operator, which can be used to check the type of an object:

```kotlin
if(obj is String) {
    print(obj.length)
}

if(obj !is String) {
    print("Not a string")
}
```

### Function References

Since Kotlin includes function types as first-class citizens, it is possible to use this type value directly. Take a named function:

```kotlin
fun isOdd(x: Int) = x % 2 != 0
```

This function can be called directly ( `isOdd(5)` ), but it can also be passed to another function using the `::` operator:

```kotlin
val numbers = listOf(1, 2, 3)
println(numbers.filter(::isOdd))
```

In this example, `::isOdd` is a value of function type `(Int) -> Boolean`.

### Property References

We can also use the `::` operator to access properties as first-class citizens:

```kotlin
val x = 1

fun main(args: Array<String>) {
    println(::x.get())
    println(::x.name)
}
```

The expression `::x` evaluates to a property of type `KProperty<Int>`, which allows us to read it value using `get()` or to retrieve its name using `name`. For mutable properties, we are also given a `set()` method.

### Constructor References

Constructors can be referenced in the same way as methods and properties. They are referenced using `::` followed by the class name.

```kotlin
class Foo

fun function(factory: () -> Foo) {
    val x: Foo = factory()
}
```

is the same as:

```kotlin
function(::Foo)
```

[Back to Home](../README.md)
