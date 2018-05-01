# Properties
## Swift
### Declaration
Declaring properties in Swift is fairly straightforward and familiar.
```Swift
class Foo {
    // an instance variable called "data" of type Int
    var data: Int

    init(data: Int){
        self.data = data
    }
}
```
```Swift
class Foo {
    // an instance variable called "data" of type Int, set to 5 by default
    var data: Int = 5

    // optional initializer
    init(data: Int){
        self.data = data
    }
}
```
In the above examples, the second declaration of the class provides a default value of the instance variable `data`. Because there is a default value, this class is not required to have an `init` method. In the first example, the `init` method is required because there is no default, and `data` isn't an optional-type, so it must be initialized to a value when the instance of the class is created.

### Constants
Declaring constants is similar to a normal instance variable.
```Swift
class Foo {
    // a constant of the class
    let hoursInDay: Int = 24

    // a class variable
    var days: Int

    init(days: Int){
        self.days = days
    }
}
```
Because this is a constant, doing the following is not allowed.
```Swift
var myFoo = Foo(days: 7)
myFoo.hoursInDay = 23
```
Any attempt to change that value, whether in the class itself or on an instance of the class will result in a compile error.

### Computed Properties
Sometimes, we want to access data like a property, but it is not necessary to store that data or to create a method simply to get that data. Computed properties allow us to access other information about a class, by gleaning it from the existing properties we have, without having to create a method. This saves memory at runtime and prevents duplication of data which can cause bugs.

From the example above, let's add a computed property that will return the number of hours for the set days we initialize it with.
```Swift
class Foo {
    let hoursInDay: Int = 24
    var days: Int

    // a read-only computed property
    var hours: Int {
        get {
            return days * hoursInDay
        }
    }

    init(days: Int){
        self.days = days
    }
}

var myFoo = Foo(days: 7)
print("There are \(myFoo.hours) hours in \(myFoo.days) days.")
// prints "There are 168 hours in 7 days."
```
As you can see, we were able to get the number of hours in 7 days without having to store this number or write a method. It was simply accessed as a computed property. Let's see what happens if we try to assign something to it.
```Swift
var myFoo = Foo(days: 7)
myFoo.hours = 24
// ERROR: Cannot assign to property: 'hours' is a get-only property
```
In order to rectify this, we must add a `set` method to this property. A computed property can have a `get` method or both a `get` and a `set` method, but not just a `set` method.
```Swift
class Foo {
    let hoursInDay: Int = 24
    var days: Int

    // a read-only computed property
    var hours: Int {
        get {
            return days * hoursInDay
        } set {
            // newValue is a keyword that contains the number on the right side of the assignment
            days = newValue / hoursInDay
        }
    }

    init(days: Int){
        self.days = days
    }
}

var myFoo = Foo(days: 7)
print("There are \(myFoo.hours) hours in \(myFoo.days) days.")
myFoo.hours = 48
print("There are \(myFoo.hours) hours in \(myFoo.days) days.")
// prints "There are 168 hours in 7 days."
// prints "There are 48 hours in 2 days."
```
### Lazy Keyword
A lazy stored property is a property whose initial value is not calculated until the first time it is used. You indicate a lazy stored property by writing the `lazy` modifier before its declaration.
```Swift
class Foo {
    lazy var date: Date = {
        print("Creating a Date object...")
        return Date()
    }()
}
```
Here, we define a lazy variable called date that is defined with a closure. This will not run until we try to do something that requires this variable to be created.
```Swift
var myFoo = Foo()
// prints nothing

print(myFoo.date)
// prints "Creating a Date object..."
// prints "2018-05-01 16:30:43 +0000"
```
This is useful for expensive operations or operations that require information that may be unknown at the time of instantiation. In this example, it is expensive to create a `Date` object, so by delaying that instantiation until it is needed, our program does not get bogged down creating the instance of `Foo`.

In contrast, let's see the same example without the lazy keyword.
```Swift
class Foo {
    var date: Date = {
        print("Creating a Date object...")
        return Date()
    }()
}

var myFoo = Foo()
// prints "Creating a Date object..."
print(myFoo.date)
// prints "2018-05-01 16:35:24 +0000"
```
## Kotlin
[Back to Home](../README.md)
