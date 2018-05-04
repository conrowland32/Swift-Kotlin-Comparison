# Comparisons
## Swift
Swift provides two main operators to do comparisons: `==` and `===` (along with their counterparts `!=` and `!==`).

### Value Equality (`==`)
To check for value equality, which is what we would normally think of as equality, we use the double equals sign `==`. This is fairly similar to other languages in its use. However, to use this on a class, the class must conform to the `Equatable` protocol.
```Swift
let x = 5
let y = 6
x == y // false
x != y // true
```

### Referential Equality (`===`)
Swift provides this to check to see if two variables contain the same reference. Even if two classes are created exactly identically, this check can still fail because they exist in two different places in memory, meaning their two references are not the same.

Let's see an example of how all of this fits together.
```Swift
class MyClass: Equatable {
    let myProperty: String

    init(s: String) {
        myProperty = s
    }
}

//implement this so we can use '==' on instances of the class
func ==(lhs: MyClass, rhs: MyClass) -> Bool {
    return lhs.myProperty == rhs.myProperty
}

var myClass1 = MyClass(s: "Hello")
var myClass2 = MyClass(s: "Hello")

print(myClass1 == myClass2) // true
print(myClass1 != myClass2) // false
print(myClass1 === myClass2) // false
print(myClass1 !== myClass2) // true

myClass1 = myClass2

print(myClass1 == myClass2) // true
print(myClass1 === myClass2) // true
```

## Kotlin
[Back to Home](../README.md)
