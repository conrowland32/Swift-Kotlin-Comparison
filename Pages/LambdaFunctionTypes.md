# Lambda Expressions, Closures, and Functions as Types

## Swift

---

## Kotlin

In Kotlin, functions are treated as first-class members. This means that they have their own types, can be stored in variables, and can be passed as parameters to other functions. This allows Kotlin functions to have a wide range of functionality.

### Function Types

Kotlin uses a variety of function types of the form `(Int) -> String`. These types consist of parenthesized parameter types list and a return type. For example, `(A, B) -> C` is a type that takes two arguments of types `A` and `B` and returns a value of type `C`. Optionally, these types can include the names of the parameters, i.e., `(a: Int, b: Int) -> Int`.

Functions can be instantiated and assigned to a variable to be used later:

```kotlin
fun double(x: Int): Int {
    return 2 * x
}
```

Functions can then be implemented in a standard way:

```kotlin
val result = double(2)
```

Function parameters are also allowed to have default values, which will be used if a parameter is omitted from the function call:

```kotlin
fun read(b: Array<Byte>, off: Int = 0, len: Int = b.size) {

}
```

Functions in Kotlin can also be declared outside of a class. This allows for the creation of package-level classes that can be accessed from anywhere.

### Lambda Functions

Lambda functions or other anonymous functions are not declared, but passed directly as an expression. For example:

```kotlin
max(strings, { a, b -> a.length < b.length })
```

In this example, `max` is a function that takes a function as its second argument. This parameter is equivalent to the named function:

```kotlin
fun compare(a: String, b: String): Boolean = a.length < b.length
```

The full form of lambda expressions is:

```kotlin
val sum = { x: Int, y: Int -> x + y }
```

If the last parameter of a function accepts function, a lambda for this argument can be placed in a block outside the parantheses:

```kotlin
val product = items.fold(1) { acc, e -> acc * e }
```

It is also interesting to note that for lambda functions with only one parameter, you are allowed to not declare the parameter:

```kotlin
ints.filter { it > 0 }
```

By default, lambdas will return the value of the last expression. If you would like to explicitly return a value other than the last expression in the lambda, you can use the _qualified return_ syntax:

```kotlin
ints.filter {
    val shouldFilter = it > 0
    shouldFilter
}

ints.filter {
    val shouldFilter = it > 0
    return@filter shouldFilter
}
```

Therefore, both the functions in the previous example will return the same.

### Closures

In Kotlin, a lambda expression or other anonymous function can access its _closure_, or the variables declared in the outer scope. These values can also be modified inside the lambda:

```kotlin
var sum = 0
ints.filter { it > 0 }.forEach {
    sum += it
}
```

[Back to Home](../README.md)
