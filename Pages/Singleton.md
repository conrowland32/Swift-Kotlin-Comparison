# Singletons
## Swift
Singletons in Swift are similar to any other OO language. They are declared as follows.
```Swift
class SomeSingleton {
    static let instance = SomeSingleton()
    ...
}
```
This can be referenced elsewhere by simply `SomeSingleton.instance`. In addition, the `lazy` keyword can be added to the `instance` constant. This will delay creation of the object until it is utilized. 

## Kotlin
[Back to Home](../README.md)
