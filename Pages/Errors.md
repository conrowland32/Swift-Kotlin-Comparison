# Errors and Exception Handling

## Swift
### Creating Error Types
In Swift, classes and enums can be thrown as an error if and only if they follow the `Error` protocol.
```Swift
// a basic error class
class MyError: Error {
    var data: Int

    init(data: Int){
        self.data = data
    }
}
```

For a group of similar errors, an enum can be useful.
```Swift
// a basic group of related errors, 2 with no data, 1 with data
enum RelatedErrors : Error {
    case Error1
    case Error2
    case Error3(message: String)
}
```

### Throwing an Error
In Swift, an error is thrown with the `throw` keyword. A function that throws an error is called a *throwing function* and requires the keyword `throws` to be placed after the function parameters and before the return arrow `->`.

```Swift
func throwsAnError(data: Double) throws -> Double {
    if(data < 0) {
        throw RelatedErrors.Error3(message: "Data cannot be negative")
    } else {
        return sqrt(data)
    }
}
```

### Handling an error
When a function throws an error, it is necessary to call that function accordingly. In Swift, this is done through a `do catch` block.
```Swift
let myData: Double = 5.0
do {
    try print(throwsAnError(data: myData))
} catch RelatedErrors.Error3(let message) {
    print(message)
}
// prints 2.23606797749979

let myData1: Double = -1.0
do {
    try print(throwsAnError(data: myData1))
} catch RelatedErrors.Error3(let message) {
    print(message)
}
// prints "Data cannot be negative"
```

---

## Kotlin

Kotlin uses Exceptions to handle thrown errors. All exception classes are descendants of the `Throwable` class. Each exception will always include a message, a stack trace, and an optional clause.

Exceptions are thrown using the `throw` keyword:

```kotlin
throw MyException("Exception thrown.");
```

Exceptions can also be used in try-catch blocks:

```kotlin
try {
    //application code
} catch (ex: MyException) {
    //exception handler
}
```

It is important to note that all exceptions in Kotlin are unchecked; there are no checked exceptions.

In Kotlin, `throw` is an expression of type `Nothing`. This type does not hold values, but can be used to mark locations in code that can never be reached. For example, `Nothing` can be used to indicate that a desired function is never intended to return:

```kotlin
fun fail(message: String): Nothing {
    throw IllegalArgumentException(message)
}
```

When this function is called, the compiler knows that the execution will not continue after it is called. Therefore, it can be used as a logical breakpoint:

```kotlin
val s = person.name ?: fail("No name")
println(s)   //if the code reaches this point, we know 's' must be initialized
```

[Back to Home](../README.md)
