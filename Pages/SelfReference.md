# Instance Self-Reference

## Swift

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
