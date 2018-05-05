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
---
## Kotlin

Kotlin supports both coroutines and threading. Coroutines are not technically multithreading, as all the computation may still occur in a single thread, but they are worth mentioning since they provide a (simple) way of running non-blocking asynchronous code. Coroutines can also be used in combination with threads as a way to asynchronously assign new tasks to threads.

Implementation of threads is included in the Kotlin standard library under `kotlin.concurrent`. This library contains the following `thread` function:

```kotlin
fun thread(
    start: Boolean = true,
    isDaemon: Boolean = false,
    contextClassLoader: ClassLoader? = null,
    name: String? = null,
    priority: Int = -1,
    block: () -> Unit
): Thread
```

This function will create and return a thread that runs the code specified in `block`. For the most simple application of this extension function, using all default parameters, the implementation becomes quite simple:

```kotlin
thread() {
    //thread code
}
```

This is a much clearer and more concise implementation of threads than in Java. However, since threads are a very expensive resource to create, and can cause some serious problems if mishandled, coroutines should be preferred for most applications.

[Back to Home](../README.md)
