# Namespaces

## Swift
In popular OO Languages like Java and C#, there is a notion of namespaces. In Java this is achieved using the `package` keyword, while C# reserves the `namespace` keyword. However, in Swift there is no notion of namespaces. Swift considers everything to be part of one namespace, which is the entire module. In essence, a module is a complete piece of work, commonly an application or framework. Let's see what the Apple Swift manual says about modules.
> A module is a single unit of code distribution—a framework or application that is built and shipped as a single unit and that can be imported by another module with Swift’s import keyword.
>
> Each build target (such as an app bundle or framework) in Xcode is treated as a separate module in Swift. If you group together aspects of your app’s code as a stand-alone framework—perhaps to encapsulate and reuse that code across multiple applications—then everything you define within that framework will be part of a separate module when it’s imported and used within an app, or when it’s used within another framework.
>
> A source file is a single Swift source code file within a module (in effect, a single file within an app or framework). Although it’s common to define individual types in separate source files, a single source file can contain definitions for multiple types, functions, and so on.

Swift does not have the capability to explicitly declare which context a class or function is defined in like Java or C#, but it does provide a way to resolve conflicts resulting from these types of issues. This is done through access control using access level modifiers. Swift provides five different access levels: `open`, `public`, `internal`, `fileprivate`, and `private`. To see more about these access levels, the [documentation](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/AccessControl.html#AccessLevels) for these describes them in more detail.

---

## Kotlin

Kotlin uses packages to define namespaces. Any source file can start with a package declaration:

```kotlin
package foo.bar
```

All the contents of the file (classes, functions, etc.) will be contained by the declared package:

```kotlin
package foo.bar

fun baz() {}

class Goo() {}
```

In the above example, both the function `baz` and the class `Goo` are members of `foo.bar`. Their full names will be `foo.bar.baz` and `foo.bar.Goo`.

If a package is not specified, the contents of the file will belong to a default package with no name.

Each file can contain its own `import` directives. We can import a single name:

```kotlin
import foo.Bar
```

We can also import all the contents of a scope:

```kotlin
import foo.*
```

The `import` keyword can be used to import classes, functions, properties, and enumerations.

[Back to Home](../README.md)
