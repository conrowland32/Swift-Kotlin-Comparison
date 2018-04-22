# Types
## Swift
### Basic Types
- Integer (`Int`)
- Float (`Float`)
- Double (`Double`)
- Boolean (`Bool`)
- String (`String`)
- Character (`Character`)

### Type Inference
In Swift, you don't have to explicitly declare what kind of variable you are creating, it is optional.
```Swift
// x is of type Int
var x = 5

// if, however, you want a variable like this to be a Double
var y: Double = 5
```

### Unique Types
Beyond the 6 basic types Swift offers, there are also some built-in complex types.

#### Tuples
In Swift, a variable can be assigned a group of multiple values.
```Swift
// it can hold 2 values...
var myTuple = (1, 5)

// ...or three values...
var myOtherTuple = (2, 4, 6)

// ...or many values
var myOtherOtherTuple = (1, 2, 3, 4, 5, 6, 7, 8, 9)

// However, the following is invalid
myTuple = myOtherTuple

// myTuple is inferred to be of type (Int, Int), so we cannot assign a value that is of type (Int, Int, Int) to it.
// This is equivalent of trying to assign a String to an Int, the two tuples are completely different.
```

#### Dictionaries
In Swift, creating a dictionary (or a map) is straightforward.
```Swift
// This is now a dictionary of type [Int: String]
let numberNames = [1: "one", 2: "two", 3: "three"]

// To access values using a key, use [] subscripts
var oneAsString = numberNames[1]

// So now oneAsString is a String type right? Not quite!
// The value returned from a lookup in a dictionary is always the value type defined in the array, but as an optional.
// So here, oneAsString is inferred to be of type String?.
// To print, we do the following

if let result = oneAsString {
  print(result)
}
// prints "one"
```

#### Functions
Yes, in Swift, functions are a type. Functions are treated as first-class members in Swift.
```Swift
// if I want a variable to hold a function, I can simply do
var aFunction: (String, String) -> String

// now define a simple function that takes 2 strings and returns one
func concat(_ first: String, _ second: String) -> String {
    return first+second
}

// assign the function name to the function variable
aFunction = concat

// use the function variable just as you would use the name of a function you explicitly define
print(aFunction("Hello", " World"))

// prints "Hello World"
```
This is a brief introduction, we go into more detail in [this section](LambdaFunctionTypes.md).


## Kotlin
[Back to Home](../README.md)
