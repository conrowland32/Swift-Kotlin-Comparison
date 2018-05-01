# Inheritance/Extension

## Swift

---

## Kotlin

Every class in Kotlin inherits from the common superclass `Any`. Any class with no superclass explicitly declared will inherit directly from `Any`. To declare a different superclass, we give the type after a `:` at the end of the class header:

```kotlin
open class Parent(p: Int)

class Child(p: Int) : Parent(p)
```

It is important to note that in Kotlin, unlike most other OO languages, all classes are `final` by default. They must explicitly be tagged with the `open` keyword in order to be inherited from.

If the child class has a primary constructor, the base class _must_ be initialized there, using the parameters of the primary constructor. If the child class has only secondary constructors, then each one must initialize the base type. The constructor of the parent class is accessed through the `super` keyword:

```kotlin
class MyView : View() {
    constructor(ctx: Context) : super(ctx)
}
```

Any other properties (with applicable access modifiers) of the parent class can also be accessed through the `super` keyword.

### Overriding

Much like classes as a whole, functions in classes are also `final` by default and must be tagged with `open` in order to be overriden:

```kotlin
open class Parent {
    open fun v() {}   //open for override
    fun nv() {}   //not open, so can not be overriden
}

class Child : Parent() {
    override fun v() {}
}
```

Properties can also be overriden in Kotlin. Overriden properties must have a compatible type. Declared properties can be a property with an initializer or a custom getter method:

```kotlin
open class Foo {
    open val x: Int get() {}
}

class Bar1 : Foo() {
    override val x: Int = ...
}
```

### Extension

Kotlin provides the ability to extend a class without the use of inheritance or a design pattern like Decorator. This allows a simple way for developers to add new functionality to an existing class. Both functions and properties can be extended onto a class. Extensions do not modify the class they extend. Extensions also have scope, so they can be written to be made available only within one class or file, or written to be made available anywhere in a package.

Extensions are covered in the [inheritance and extension section](./InheritanceExtension).

To declare an extension function, we can simply prefix its name with the type we want to extend. For example, to add a `swap` function to `MutableList<Int>`:

```kotlin
fun MutableList<Int>.swap(index1: Int, index2: Int) {
    val tmp = this[index1]
    this[index1] = this[index2]
    this[index2] = tmp
}
```

Now, the `swap` function will be available as if it were a function created within the `MutableList<Int>` class. In a similar vein, we can also declare extension properties:

```kotlin
val <T> List<T>.lastIndex: Int
    get() = size - 1
```

[Back to Home](../README.md)
