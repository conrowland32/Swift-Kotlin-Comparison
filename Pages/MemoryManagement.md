# Memory Management

## Swift

---

## Kotlin

Since Kotlin is designed to run on a variety of different targets (JVM, LLVM, JavaScript transcription) it is difficult to nail down the way the Kotlin handles memory management. For the version of Kotlin that is interoperable with Java and targets the JVM, Kotlin does not do any of its own memory management; it allows the JVM to handle all of the memory allocation and deallocation. This means that it runs with the same garbage collecter that standard Java code does.

However, JetBrains is currently working on a new project, Kotlin native, which is a version of Kotlin which compiles directly to native binaries without the use of any VM. It is designed to provide an implementation of Kotlin on platforms where it is not desirable or possible to use a VM. For this project, JetBrains has announced that Kotlin will use automatic reference counting wherever possible, with cyclic garbage collector on top.

[Back to Home](../README.md)
