# Interfaces/Protocols

## Swift

---

## Kotlin

Kotlin uses an implementation of interfaces very similar to that of Java. Kotlin interfaces an contain abstract method declarations and full method implementations. The only difference between interfaces and abstract classes is that interfaces cannot store state. Interfaces are created using the `interface` keyword:

```kotlin
interface MyInterface {
    fun bar()
    fun foo() {

    }
}
```

Classes or objects can implement one or more interface by declaring it at the end of the function header:

```kotlin
class Child : MyInterface {
    override fun bar() {

    }
}
```

It is possible to declare properties in an interface. These properties must either be abstract or provide implementations for accessors. Non-abstract properties do not necessarily have to be overriden in classes which implement the interface. However, properties declared in interfaces can't have backing fields:

```kotlin
interface MyInterface {
    val prop: Int   //abstract property

    val propertyWithImplementation: String
        get() = "foo"

    fun foo() {
        print(prop)
    }
}
```

[Back to Home](../README.md)
