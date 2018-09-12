# Classes

## Swift
As a multi-paradigm language, Swift offers the ability to create classes just as any other object-oriented language allows you to as well. Let's look at the creation and instantiation of a simple Swift class.

```Swift
class Person {

    // instance variables
    var first: String
    var last: String
    var age: Int

    // initializer
    init(first: String, last: String, age: Int){
        self.first = first
        self.last = last
        self.age = age
    }

    // methods
    func printDescription() -> Void {
        print("\(self.first) \(self.last) is \(self.age) years old.")
    }
}
```
The initializer, or constructor in other languages, is defined by the function named `init`. To create an instance of this `Person` class, we simply do the following
```Swift
var somePerson = Person(first: "Logan", last: "Harrison", age: 21)
```
By writing `Person(...)` we are saying we would like an instance of class `Person`, which automatically calls the `init` method. Now that we have an instance of the class, we can use its functionality.
```Swift
somePerson.printDescription()
// prints "Logan Harrison is 21 years old."
```
### Failable Initializers
One interesting property of Swift classes is the notion of failable initializers. This prevents an object getting created with properties that don't logically make sense. For example, let's look at the modified `Person` class.

```Swift
class Person {

    // instance variables
    var first: String
    var last: String
    var age: Int

    // initializer
    init?(first: String, last: String, age: Int){
        if age < 0 || age > 120 {
            return nil
        }
        self.first = first
        self.last = last
        self.age = age
    }

    // methods
    func printDescription() -> Void {
        print("\(self.first) \(self.last) is \(self.age) years old.")
    }
}
```
This initializer now will only allow the creation of a `Person` object if the age parameter is between 0-120. If the age parameter isn't in this range, the object created will be `nil`.
```Swift
if let somePerson = Person(first: "Logan", last: "Harrison", age: 21) {
    somePerson.printDescription()
}
// prints "Logan Harrison is 21 years old."

if let somePerson = Person(first: "Logan", last: "Harrison", age: -1) {
  somePerson.printDescription()
}
// prints nothing
```
### Computed Properties
Another interesting functionality of Swift classes are the ability to use computed properties. A computed property allows for properties to be computed when they are needed instead of being stored or having to have a separate function call for them.
```Swift
class Person {

    // instance variables
    var first: String
    var last: String
    var age: Int
    var numLetters: Int {
        get {
            return first.count + last.count
        }
    }

    // initializer
    init(first: String, last: String, age: Int){
        self.first = first
        self.last = last
        self.age = age
    }

    // methods
    func printNumLetters() -> Void {
        print("There are \(numLetters) letters in \(self.first) \(self.last).")
    }
}
```
Here, `numLetters` is a computed property. Anytime this property is accessed, the `get` method is called. In addition to `get`, there can also be a `set` method. When a property only has a `get` method it is considered read-only. Let's see the use of this property.
```Swift
var somePerson = Person(first: "Logan", last: "Harrison", age: 21)
somePerson.printNumLetters()
// Prints "There are 13 letters in Logan Harrison."

// change the last name
somePerson.last = "Smith"
somePerson.printNumLetters()
// prints "There are 10 letters in Logan Smith."
```
Even after changing the last name, we do not have to do any separate calculations to get the number of letters because it is done at runtime.

### Classes *vs* Structs
In Swift, we have the option to create either structs or classes. For the most part, these are interchangeable. Structs can have functions, initializers, and computed properties just like classes. The major difference is that `class` is a reference type while `struct` is a value type. To see this, let's look at the following example.
```Swift
class PersonClass {

    var name: String

    init(name: String){
        self.name = name
    }
}

struct PersonStruct {

    var name: String

    init(name: String){
        self.name = name
    }
}

var classA = PersonClass(name: "Bob")
var classB = classA
classB.name = "Sue"

print(classA.name) // prints "Sue"
print(classB.name) // prints "Sue"

var structA = PersonStruct(name: "Bob")
var structB = structA
structB.name = "Sue"

print(structA.name) // prints "Bob"
print(structB.name) // prints "Sue"
```
As we can see, `classA` and `classB` both reference the same object, hence why changing `classB` affects `classA`. However, this behavior doesn't happen for structs. Doing the assignment `var structB = structA` creates a new struct with the same values as `structA`.

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
