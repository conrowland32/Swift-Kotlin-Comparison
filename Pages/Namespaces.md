# Namespaces
## Swift
In popular OO Languages like Java and C#, there is a notion of namespaces. In Java this is achieved using the `package` keyword, while C# reserves the `namespace` keyword. However, in Swift there is no notion of namespaces. Swift considers everything to be part of one namespace, which is the entire module. In essence, a module is a complete piece of work, commonly an application or framework. Let's see what the Apple Swift manual says about modules.
> A module is a single unit of code distribution—a framework or application that is built and shipped as a single unit and that can be imported by another module with Swift’s import keyword.
>
> Each build target (such as an app bundle or framework) in Xcode is treated as a separate module in Swift. If you group together aspects of your app’s code as a stand-alone framework—perhaps to encapsulate and reuse that code across multiple applications—then everything you define within that framework will be part of a separate module when it’s imported and used within an app, or when it’s used within another framework.
>
> A source file is a single Swift source code file within a module (in effect, a single file within an app or framework). Although it’s common to define individual types in separate source files, a single source file can contain definitions for multiple types, functions, and so on.

Swift does not have the capability to explicitly declare which context a class or function is defined in like Java or C#, but it does provide a way to resolve conflicts resulting from these types of issues. This is done through access control using access level modifiers. Swift provides five different access levels: `open`, `public`, `internal`, `fileprivate`, and `private`. To see more about these access levels, the [documentation](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/AccessControl.html#AccessLevels) for these describes them in more detail.

## Kotlin
[Back to Home](../README.md)
