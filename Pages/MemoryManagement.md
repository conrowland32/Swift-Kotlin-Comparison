# Memory Management
## Swift
As we previously stated, Swift does not allow developers to directly manage memory or pointers like its predecessor Objective-C does. Not only does this prevent headaches when programming, it ensures that memory is managed efficiently. To see how memory is managed by Swift, let's look at the documentation regarding memory management.

> Swift uses *Automatic Reference Counting* (ARC) to track and manage your app’s memory usage. In most cases, this means that memory management “just works” in Swift, and you do not need to think about memory management yourself. ARC automatically frees up the memory used by class instances when those instances are no longer needed.
> Every time you create a new instance of a class, ARC allocates a chunk of memory to store information about that instance. This memory holds information about the type of the instance, together with the values of any stored properties associated with that instance.
> To make sure that instances don’t disappear while they are still needed, ARC tracks how many properties, constants, and variables are currently referring to each class instance. ARC will not deallocate an instance as long as at least one active reference to that instance still exists.

Note that a difference between `struct` and `class` arises here as well. Since structs are *value-types*, they are not managed by ARC because they do not handle references.

To see ARC in action, let's look at the following example.
```Swift
class Person {
    let name: String
    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }
    deinit {
        print("\(name) is being deinitialized")
    }
}

var reference1: Person?
var reference2: Person?

reference1 = Person(name: "Logan")
reference2 = Person(name: "Connor")

// "Logan" instance has no references anymore, ARC deinitializes it
reference1 = reference2

/*
 prints:

 Logan is being initialized
 Connor is being initialized
 Logan is being deinitialized
*/
```

## Kotlin
[Back to Home](../README.md)
