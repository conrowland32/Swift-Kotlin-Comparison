# Classes

## Swift

---

## Kotlin

Classes are declared using the `class` keyword.

```kotlin
class Invoice {

}
```

### Constructors

In Kotlin, classes have a primary constructor and can also have one or more secondary constructors. The primary constructor is part of the header when the class is defined:

```kotlin
class Person constructor(firstName: String) {

}
```

The code to initialize the class using the primary constructor is given in initializer blocks denoted by the `init` keyword. The initializers are executed in the order they appear within the class. It is also possible to declare and initialize properties in the primary constructor:

```kotlin
class Person(val firstName: String, val lastName: String, var age: Int) {

}
```

Secondary constructors are denoted by the the `constructor` keyword, and can take a different set of parameters from the primary constructor. However, every secondary constructor **must** delegate to the primary constructor using the `this` keyword.

```kotlin
class Person(val name: String) {
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}
```

If a non-abstract class has no constructor, it will automatically generate a no-argument constructor. In order to make a class without a public constructor, you must explicitly create a _private_ constructor on the class.

### Instantiation

To instantiate a class in Kotlin, call the constructor as if it were any other function:

```kotlin
val invoice = Invoice()

val customer = Customer("Joe Smith")
```

Unlike many OO languages, Kotlin does not use a `new` keyword for instantiation.

### Inheritance

Class inheritance, extension, and overriding is covered in the [Inheritance Section](./InheritanceExtension).

### Abstract Classes

A class and its members can be declared as `abstract`. Any `abstract` members do not include their full implementation. `Abstract` classes cannot be instantiated, and are `open` by default.

### Companion Objects

Unlike many OO languages, Kotlin does not allow classes to have `static` methods. Instead, stand-alone functions can be created on the package level. In order to write a function that can access the properties of a class (such as a factory method), you can declare a companion object within the class. This will allow calling of its members using the typical dot notation used for `static` methods in other OO languages.

[Back to Home](../README.md)
