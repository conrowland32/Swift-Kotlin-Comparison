# Lambda Expressions, Closures, and Functions as Types
## Swift
### Function Types
Swift treats functions as first class members. One can declare a variable that holds a function the same as declaring a variable to hold an integer.
```Swift
// define a variable that is a function that takes two ints and returns an int
var myMathFunction: (Int, Int) -> Int

// two basic functions
func sum(_ a: Int, _ b: Int) -> Int {
    return a+b
}

func minus(_ a: Int, _ b: Int) -> Int {
    return a-b
}

myMathFunction = sum
print(myMathFunction(3,5)) // 8

myMathFunction = minus
print(myMathFunction(3,5)) // -2
```

Function types can also be used for parameters.
```Swift
// two basic functions
func sum(_ a: Int, _ b: Int) -> Int {
    return a+b
}

func minus(_ a: Int, _ b: Int) -> Int {
    return a-b
}

func perform(operation: (Int, Int) -> Int, on x: Int, and y: Int) -> Int {
    return operation(x, y)
}

let result = perform(operation: sum, on: 3, and: 4)
print(result)
```

### Lambda Expressions
Lambda expressions in Swift are extremely similar to using function types.
```Swift
func perform(on x: Int, and y: Int, operation: (Int, Int) -> Int) -> Int {
    return operation(x, y)
}

let result = perform(on: 3, and: 4) {
    return $0+$1
}
print(result)
```
Any time a function takes another function, you can use a lambda at the end of the call to define that function.

### Closures
One common place closures occur in Swift is the `sorted` method.
```Swift
let numbers = [1, 4, 2, 7, 10, 3, 5]

let sortedNumbers = numbers.sorted(by: { (num1: Int, num2: Int) -> Bool in return num1 < num2 })

print(sortedNumbers)
// prints [1, 2, 3, 4, 5, 7, 10]
```

The part inside the brackets `{}` is a closure. This is used to define a block of code that will be used by the sorted method to sort the numbers in the array.

## Kotlin
[Back to Home](../README.md)
