# Singletons

## Swift
Singletons in Swift are similar to any other OO language. They are declared as follows.
```Swift
class SomeSingleton {
    static let instance = SomeSingleton()
    ...
}
```
This can be referenced elsewhere by simply `SomeSingleton.instance`. In addition, the `lazy` keyword can be added to the `instance` constant. This will delay creation of the object until it is utilized. 

---

## Kotlin

Singletons can be created in Kotlin through _object declaration_ using the `object` keyword:

```kotlin
object DataProviderManager {
    fun registerDataProvider(provider: DataProvider) {

    }

    val allDataProviders: Collection<DataProvider>
        get() = // ...
}
```

This allows a singleton to be created of any type. After creation, we can refer to the object by its name directly:

```kotlin
DataProviderManager.registerDataProvider(...)
```

If the object is created at a package level, it can be referenced and utilized anywhere in the package.

[Back to Home](../README.md)
