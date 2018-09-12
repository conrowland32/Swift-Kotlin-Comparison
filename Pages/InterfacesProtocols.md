# Interfaces/Protocols

## Swift
Swift uses protocols to ensure that classes provide certain functionality. Protocols are functionally identical to Java interfaces and Kotlin interfaces.
### Declaration
Declaring a protocol is pretty simple.
```Swift
protocol MyProtocol {
    func foo()
    func bar()
}
```
This is a very simplified protocol. Protocols can also contain information about what kind of properties must be in the conforming class.
```Swift
protocol FullyNamed {
    // required to have a property named "fullName" that has a getter
    var fullName: String { get }
}

protocol Identifiable {
    // required to have a property named "id" that has a getter and a setter
    var id: Int { get set }
}
```
### Following Protocols
To declare that a class will follow or conform to a protocol, simple place a colon after the class name, then all of the protocols it will conform to separated by commas.
```Swift
class MyClass : MyProtocol {
    func foo() {
        // intentionally blank
    }

    func bar() {
        // intentionally blank
    }
}
```
If this class does not implement a `foo()` and a `bar()` method, an error will be shown.

In this example, class `Person` conforms to two protocols.
```Swift
protocol FullyNamed {
    var fullName: String { get }
}

protocol Identifiable {
    var id: Int { get set }
}

class Person : FullyNamed, Identifiable {
    var fullName: String
    var id: Int

    init(fullName: String, id: Int){
        self.fullName = fullName
        self.id = id
    }
}
```
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
