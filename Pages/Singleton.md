# Singletons

## Swift

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
