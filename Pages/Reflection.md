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

---

## Kotlin

Kotlin includes several ways to reflect on both functions and properties.

### Class References

Kotlin allows you to retrieve the runtime reference to a Kotlin class using the _class literal_ syntax:

```kotlin
val c = MyClass::class
```

Kotlin also includes the `is` operator, which can be used to check the type of an object:

```kotlin
if(obj is String) {
    print(obj.length)
}

if(obj !is String) {
    print("Not a string")
}
```

### Function References

Since Kotlin includes function types as first-class citizens, it is possible to use this type value directly. Take a named function:

```kotlin
fun isOdd(x: Int) = x % 2 != 0
```

This function can be called directly ( `isOdd(5)` ), but it can also be passed to another function using the `::` operator:

```kotlin
val numbers = listOf(1, 2, 3)
println(numbers.filter(::isOdd))
```

In this example, `::isOdd` is a value of function type `(Int) -> Boolean`.

### Property References

We can also use the `::` operator to access properties as first-class citizens:

```kotlin
val x = 1

fun main(args: Array<String>) {
    println(::x.get())
    println(::x.name)
}
```

The expression `::x` evaluates to a property of type `KProperty<Int>`, which allows us to read it value using `get()` or to retrieve its name using `name`. For mutable properties, we are also given a `set()` method.

### Constructor References

Constructors can be referenced in the same way as methods and properties. They are referenced using `::` followed by the class name.

```kotlin
class Foo

fun function(factory: () -> Foo) {
    val x: Foo = factory()
}
```

is the same as:

```kotlin
function(::Foo)
```

[Back to Home](../README.md)
