# 1.Comparing Classes and Structures   
Classes and structures in Swift have many things in common. Both can:

- Define properties to store values
- Define methods to provide functionality
- Define subscripts to provide access to their values using subscript syntax
- Define initializers to set up their initial state

Classes have additional capabilities that structures do not:

- Inheritance enables one class to inherit the characteristics of another.
- Type casting enables you to check and interpret the type of a class instance at runtime.
- Deinitializers enable an instance of a class to free up any resources it has assigned.
- Reference counting allows more than one reference to a class instance.

# 2.判断是否为同一引用
```swift
let tenEighty = VideoMode()
let alsoTenEighty = tenEighty

if tenEighty === alsoTenEighty {
    print("tenEighty and alsoTenEighty refer to the same VideoMode instance.")
}
// Prints "tenEighty and alsoTenEighty refer to the same VideoMode instance."
```

# 3.Assignment and Copy Behavior for Strings, Arrays, and Dictionaries
In Swift, many basic data types such as String, Array, and Dictionary are implemented as **structures**. This means that data such as strings, arrays, and dictionaries are copied when they are assigned to a new constant or variable, or when they are passed to a function or method.

This behavior is different from Foundation: NSString, NSArray, and NSDictionary are implemented as **classes**, not structures. Strings, arrays, and dictionaries in Foundation are always assigned and passed around as a reference to an existing instance, rather than as a copy.
