# Listeners and Event Handlers
## Swift
Swift tackles listeners and event handlers in a unique way. Swift has a notion of *delegation*, assigning one object the responsibility of handling certain tasks for another. Delegation relies on the use of *protocols* heavily. Say you have a property or a UI element that needs an event listener, you would define a delegate protocol that lists the methods that the listener will access. You then have the option to either handle that internally in the class or file that is utilizing that element, or you can created an external class. The delegate for the object will either be set to `self` if you choose to handle them in the same place, or will be set to a reference of the delegate object you create. Either way, the delegate must conform to the delegate protocol that is defined, so the methods are guaranteed to be defined. Examples of this can be seen in many UI elements in the iOS framework.
## Kotlin
[Back to Home](../README.md)
