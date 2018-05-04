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

## Kotlin
[Back to Home](../README.md)
