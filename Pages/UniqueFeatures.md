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

print(myOtherOptional!)
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

### Assignments Return no value
In popular languages like C and Java, the statement `x = 5` returns a value. However, in Swift, assignments do not return a value. By doing so, or by not doing so rather, Swift stops common bugs dealing with assignments. For instance, a common mistake in programming is the following.

```Java
int x = 5;
if (x = 4){
  System.out.println("x is equal to 4");
}
// prints "x is equal to 4"
```
Even though it is obvious that this is not true, because of the bug with `x = 4` instead of `x == 4`, the program says that 5 is equal to 4. This is because the assignment of `x = 4` returns `true`, which causes the `if` statement to execute. Let's see what happens in Swift.
```Swift
var x = 5
if (x = 4){
  print("x is equal to 4")
}
// Error: Use of '=' in a boolean context, did you mean '=='?
```
Swift has prevented this bug from occurring.

### Range Operator
Swift has gotten rid of C-style for loops (`for (int i=0; i<n; i++)`) and instead has replaced them with a range operator. Ranges can be assigned to a variable, or explicitly written where needed. Let's look at a couple different types of ranges.
#### Closed Range
```Swift
for i in 0...5 {
  print(i)
}
// prints 0 1 2 3 4 5
```
#### Half-Open Range
```Swift
for i in 0..<5 {
  print(i)
}
// prints 0 1 2 3 4
```
#### One-Sided Range
```Swift
let range = 0...

range.contains(1) // true
range.contains(0) // true
range.contains(-1) // false

for i in range {
  print(i)
}
// prints 0 1 2 3 4 5 6 7 ... for as long as the program runs
```
One-sided ranges can also have an upper bound instead of a lower bound.
```Swift
let range = ...0

range.contains(1) // false
range.contains(0) // true
range.contains(-1) // true

for i in range {
  print(i)
}
// Error: range does not conform to protocol "Sequence"
```
One-sided ranges can also be open at the top (but not the bottom) bound.
```Swift
let range = ..<0

range.contains(1) // false
range.contains(0) // false
range.contains(-1) // true

for i in range {
  print(i)
}
// Error: range does not conform to protocol "Sequence"
```
#### Iterating Over Arrays Using Ranges
In Swift, it is possible to iterate over arrays using ranges.
```Swift
let array = [0, 1, 2, 3, 4, 5, 6]

var range = 2...4
print(array[range])
// prints [2, 3, 4]

range = 2...
print(array[range])
// prints [2, 3, 4, 5, 6]

range = ...5
print(array[range])
// prints [0, 1, 2, 3, 4, 5]

range = 1..<6
for element in array[range] {
  print(element)
}
// prints 1 2 3 4 5
```

### Other Unique Features
- Statements do not need to end in semi-colons
- Uses inferred types
- Functions are first-class members
- Strings, even identifiers fully support unicode (yes, that means emojis too)

## Kotlin
[Back to Home](../README.md)
