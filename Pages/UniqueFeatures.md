# Unique Language Features
## Swift
### Optionals
Optionals are perhaps the most unique feature of Swift. Optional values are values that can contain null. Optionals have a notion of being wrapped (i.e. the variable is "in a box"). To get the value of the variable "out of the box" you must "unwrap" it. Unwrapping allows you to access the value in the box if it is not null. First, let's see how to declare an optional.

```Swift
// declares a String optional with an initial value of "hello"
var myOptional: String? = "hello"

// declares a String optional with an initial value of nil
var myOtherOptional: String?
```

Now, let's look at the different ways to unwrap optionals.
##### Optional Binding

```Swift
if let myValue = myOptional {
  print(myValue)
}
// prints "hello"
```
Because `myOptional` has a value, "hello", the `if` statement executes and assigns the value from `myOptional` to `myValue` for the scope of the `if` statement.

```Swift
if let myValue = myOtherOptional {
  print(myValue)
}
// prints nothing
```
Because `myOtherOptional` contains no value, nil, the `if` statement does not execute, nothing is assigned to `myValue`, and the program continues.



## Kotlin
[Back to Home](../README.md)
