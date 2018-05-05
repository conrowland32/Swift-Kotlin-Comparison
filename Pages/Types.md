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


---

## Kotlin

In Kotlin, all types are objects. However, some types have a special internal representation that allows them to be treated as primitive values at runtime. Kotlin has five basic types: numbers, characters, booleans, arrays, and strings.

### Numbers

Kotlin provides the following built-in number types:
| **Type** | **Bit Width** |
|---|:---:|
| Double | 64 |
| Float | 32 |
| Long | 64 |
| Int | 32 |
| Short | 16 |
| Byte | 8 |

Numbers support the following literal constants: Decimals (`123`), Hexadecimals (`0x0f`), and Binaries (`0b00001011`).

Every number type supports the following conversions: `toByte()`, `toShort()`, `toInt()`, `toLong()`, `toFloat()`, `toDouble()`, and `toChar()`.

### Characters

Characters are represented by the type `char`, and can not be treated directly as numbers. Character literals are placed in single quotes `'1'`. Special characters can be used with typical escape sequences such as `\t` or `\"`. Unicode characters can be encoded with the edcape syntax `\uFF00`. Characters can be explicitly cast to an `Int`.

### Booleans

Booleans are represented by the type `Boolean` and holds either `true` or `false`. Booleans include the typical logical operations `||`, `&&`, and `!`.

### Arrays

Arrays are represented by the `Array` class. They have `get` and `set` functions, and a `size` property.

Arrays can be created with the library function `arrayOf()` and a list of the items to be added. Arrays can also be created by using the constructor `Array(size, function)` passed the desired size of the array and the function that can return the initial value of each array element given its index.

### Strings

Strings are represented by the type `String`. Elements of a string are characters that can be indexed or iterated through. String can be concatenated using `+`.

In Kotlin, strings can containtemplate expressions. They are denoted by a `$` and can contain a simple name:

```kotlin
val i = 10
println("i = $i")   //prints "i = 10"
```

or an abritrary expression in curly braces:

```kotlin
val s = "abc"
println("$s.length is ${s.length}")   //prints "abc.length is 3"
```

[Back to Home](../README.md)
