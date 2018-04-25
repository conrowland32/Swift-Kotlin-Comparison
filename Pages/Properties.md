# Properties

## Swift

---

## Kotlin

### Declaration

In Kotlin, properties can be declared as mutable using the `var` keyword, or as read-only (constant) using the `val` keyword. In order to access a property, we can refer to it directly by name:

```kotlin
fun copyAddress(address: Address): Address {
    val result = Address()
    result.name = address.name
    result.street = address.street
    return result
}
```

### Getters and Setters

The syntax for declaring a property is:

```kotlin
var <propertyName>[: <PropertyType>] [= <property_initializer>]
    [<getter>]
    [<setter>]
```

The initializer, getter, and setter are optional. The property type is also optional if it can be inferred. If no getter and/or setter are given, default ones will be created. If a custom getter and/or setter is desired, they can be written right into the property declaration:

```kotlin
var stringRepresentation: String
    get() = this.toString()
    set(value) {
        setDataFromString(value)
    }
```

### Backing Fields

Fields cannot be declared directly in classes in Kotlin. However, if a field needs a backing field, Kotlin will provide it automatically. A backing field will be generated for a property if it uses the default implementation of at least one accessor, or if a custom accessor references it. Backing fields can be referenced in the accessors of the property using the `field` keyword:

```kotlin
var counter = 0
    set(value) {
        if(value >= 0) field value
    }
```

If a task requires something that does not follow the implicit backing method, it is possible to manually create a _backing property_.

### Computed Properties

Kotlin refers to its version of computed properties as _Delegated Properties_. One version of these properties are _lazy_ properties, which are only computed upon the first access. Delegated properties can be created with the following syntax:

```kotlin
var p: String by Delegate()
```

Lazy delegates take a lambda and return an instance of `Lazy<T>` which serves as the delegate. The first call to `get()` executes the lambda passed to `lazy()` and remembers the result. After the first call, subsequent calls to `get()` will simply return the remembered result, and not compute tha value again:

```kotlin
val lazyValue: String by lazy {
    println("computed")
    "Hello"
}

fun main(args: Array<String>) {
    println(lazyValue)
    println(lazyValue)
}
```

The above example will print:

```
computed
Hello
Hello
```

For a computed property that is dynamically computed _every_ time a property is accessed, we can simply create a normal property with a custom getter that defines the computation to be done each time:

```kotlin
class Banana {
    var ripeness = 5

    val color: String
        get() = when {
            ripeness > 80 -> "brown"
            ripeness > 50 -> "yellow"
            else -> "green"
        }
}
```

[Back to Home](../README.md)
