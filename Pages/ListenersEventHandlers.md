# Listeners and Event Handlers

## Swift

---

## Kotlin

In Kotlin, the line between listeners and event handlers is blurry. The most common way of implementation is to create an observable delegate. This delegate both watches for the property to be changed, and also runs a handler for modifications each time a change occurs. In a sense, observable delegates serve as both listeners and event handlers in most situations in Kotlin.

Delegates are created through `Delegates.observable()`, which takes two arguments: the initial value for the property, and a handler for any modifications to the property. The handler gets called each time a change is made, and takes three arguments itself: the property being assigned to, the old value, and the new value.

```kotlin
import kotlin.properties.Delegates

class User {
    var name: String by Delegates.observable("<no name>") {
        prop, old, new ->
        println("$old -> $new")
    }
}

fun main(args: Array<String>) {
    val user = User()
    user.name = "First name"
    user.name = "Second name"
}
```

The above example will print:

```kotlin
<no name> -> first
first -> second
```

It is also possible to intercept any assignments to the property using `vetoable()`. This will allow the handler to be called _before_ the assignment of the new property.

[Back to Home](../README.md)
