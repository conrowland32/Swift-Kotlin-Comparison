# Inheritance/Extension

## Swift
### Inheritance
To inherit from a parent class in Swift, simply place the type of the parent class after a `:` after the name of the subclass.
```Swift
class Pet {
    var name: String
    var age: Int

    init(name: String, age: Int){
        self.name = name
        self.age = age
    }

    func makeSound() -> Void {
        // empty... what sound does a pet make???
    }
}

class Dog : Pet {
    var breed: String
    init(name: String, age: Int, breed: String){
        self.breed = breed
        // calling the constructor of the superclass Pet
        super.init(name: name, age: age)
    }

    // final because no subclasses of Dog needs to change this... all dogs bark
    final override func makeSound() {
        print("*bark*")
    }
}
```

### Extension
While inheritance is a core concept of OO programming, using it too much or relying on it heavily causes messy codebases and lots of ugly, boilerplate code that takes time and can easily be prevented. In Swift, instead of always having to define a new class to add functionality, we have the ability to add an extension to an existing class, i.e. add new functionality to an existing class.

Assume we have a `Person` class defined as follows.
```Swift
class Person {
    var name: String
    var age: Int

    init(name: String, age: Int){
        self.name = name
        self.age = age
    }

    func description() -> Void {
        print("\(self.name) is \(self.age) years old.")
    }
}
```

Now, anywhere in the project we can instantiate this class. Say in one part of the project we want to check to see if the person is legally allowed to drink alcohol. Instead of adding a method to check this in the original `Person` class (breaking one of the SOLID design principles), we can add an extension in *a different file* to add this functionality.
```Swift
// adding an extension to Person in an external file
extension Person {
    func isLegal() -> Bool {
        return self.age >= 21
    }
}

var somePerson: Person = Person(name: "Logan", age: 21)
if(somePerson.isLegal()){
    print("\(somePerson.name) can legally drink.")
} else {
    print("\(somePerson.name) cannot legally drink")
}
```

While extensions cannot add stored properties to classes, they can add computed properties. So, a better way to do the above code is the following.
```Swift
extension Person {
    var isLegal: Bool {
        get {
            return self.age >= 21
        }
    }
}

var somePerson: Person = Person(name: "Logan", age: 21)
if(somePerson.isLegal){
    print("\(somePerson.name) can legally drink.")
} else {
    print("\(somePerson.name) cannot legally drink")
}
```

In addition to adding extensions to classes, Swift also allows for the extension of primitive types.
```Swift
extension Double {
    var km: Double { return self / 1000 }
    var mm: Double { return self * 1000 }
    var cm: Double { return self * 100 }
    var inches: Double { return self * 39.37 }
}

// assume we have some Double value given in meters
let fiveMeters: Double = 5.0
let fiveMetersInInches = fiveMeters.inches
print(fiveMetersInInches) // prints 196.85
let fiveMetersInKilometers = fiveMeters.km
print(fiveMetersInKilometers) // prints 0.005
```

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
