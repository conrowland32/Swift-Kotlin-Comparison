# Reflection
## Swift
Perhaps the simplest type of reflection is the `is` keyword. This checks to see if a variable is of a certain type.
```Swift
class ClassA {

}

class ClassB {

}

var objects: [Any] = [Any]()
objects.append(ClassA())
objects.append(ClassA())
objects.append(ClassB())
objects.append(ClassA())
objects.append(ClassB())

var countA: Int = 0
var countB: Int = 0

for object in objects {
    if (object is ClassA) {
        countA += 1
    } else if (object is ClassB) {
        countB += 1
    } else {
        print("Object was neither ClassA or ClassB")
    }
}

print("There are \(countA) ClassA objects and \(countB) ClassB objects.")
// prints "There are 3 ClassA objects and 2 ClassB objects."
```

For more in-depth reflection, Swift provides the [Mirror API](https://developer.apple.com/documentation/swift/mirror). This allows inspection of methods and some other high-level information. Swift does not provide a lot of options for reflection, however it does support Objective-C runtime libraries which have a lot more options for reflection. Despite this, reflection in Swift is not nearly as important as other languages because it has safeguards such as `guard let`, protocols, and optionals to help prevent errors that would be solved by reflection in other languages.

## Kotlin
[Back to Home](../README.md)
