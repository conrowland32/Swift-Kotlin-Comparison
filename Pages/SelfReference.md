# Instance Self-Reference

## Swift
In Swift, we use the `self` keyword to reference the object that we are in.
```Swift
class A {
    var data: Int

    init(data: Int) {
        self.data = data
    }
}
```
---
## Kotlin

In Kotlin, instance reference name is given by the `this` keyword:

```kotlin
class Person {
    constructor(parent: Person) {
        parent.children.add(this)
    }
}
```

In order to refer to `this` in a different scope, we can use _label qualifiers_:

```kotlin
class A {
    inner class B {
        fun Int.foo() {
            val a = this@A   //A's this
            val b = this@B   //B's this
            val c = this   //foo()'s receiver, an Int
        }
    }
}
```

[Back to Home](../README.md)
