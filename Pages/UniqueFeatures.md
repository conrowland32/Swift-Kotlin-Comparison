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

#### Unwrapping Optionals
##### Using If Statement
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

##### Force Unwrapping
```Swift
print(myOptional!)
// prints "hello"

print (myOtherOptional!)
// produces an error
```
By force unwrapping(`!`), the developer is saying, "though this is an optional, I *know* it is not nil." If the optional has a value, everything works as expected; however, if the optional does not have a value an error is produced. Force unwrapping is rarely a good idea because it defeats the purpose of using optionals.

##### Optional Chaining
```Swift
if let result = myOptional?.uppercased(){
  print(result)
}
// prints "HELLO"
```
To convert the string to uppercase we use the built-in method on the String class called "uppercased()" which returns a `String`. To access this method, we use dot notation on a `String`. However, we do not have a `String` because `myOptional` is of type `String?`. If we attempt to call `uppercased()` on `myOptional` we get an error because `myOptional` has not been unwrapped, or turned into a `String`. By adding `?` after `myOptional` before calling `uppercased()` on it, we can easily attempt to unwrap it. The `?` says, "Attempt to unwrap this optional. If it can successfully be unwrapped, meaning it contains a value, replace it with the value then proceed. If it cannot be unwrapped, because it is nil, then stop execution of the statement." The above code is functionally the same as the following.
```Swift
if let myValue = myOptional {
  let result = myValue.uppercased()
  print(result)
}
// prints "HELLO"
```
By using optional chaining (the first example), the unwrapping of `myOptional` can happen in the same line that we call `uppercased()` on it. We must use the `if let` syntax for `result` because if `myOptional` contained nil, nothing would be returned into `result`, so the following block should not execute. 




## Kotlin
[Back to Home](../README.md)
