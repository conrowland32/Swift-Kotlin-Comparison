# Listeners and Event Handlers

## Swift
Swift tackles listeners and event handlers in a unique way. Swift has a notion of *delegation*, assigning one object the responsibility of handling certain tasks for another. Delegation relies on the use of *protocols* heavily. Say you have a property or a UI element that needs an event listener, you would define a delegate protocol that lists the methods that the listener will access. You then have the option to either handle that internally in the class or file that is utilizing that element, or you can created an external class. The delegate for the object will either be set to `self` if you choose to handle them in the same place, or will be set to a reference of the delegate object you create. Either way, the delegate must conform to the delegate protocol that is defined, so the methods are guaranteed to be defined. Examples of this can be seen in many UI elements in the iOS framework.

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
