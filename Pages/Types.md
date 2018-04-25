# Types

## Swift

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
