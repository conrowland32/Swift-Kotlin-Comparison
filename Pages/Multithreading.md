# Multithreading
## Swift
Unlike other OO languages, Swift tackles the threading problem without involving extending a class or following a protocol. Swift uses `DispatchQueue` as a main starting point for all threading activities. The easiest way to see this in action is to look at an example.

```Swift
DispatchQueue.global(qos: .background).async {
    print("This is run on the background queue")

    DispatchQueue.main.async {
        print("This is run on the main queue, after the previous code in outer block")
    }
}
```
## Kotlin
[Back to Home](../README.md)
