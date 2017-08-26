# 1.可自行定义构成方法
```swift
class Car {
    init(color: String) {
        print(color)
    }
    
    init(type: String) {
        print(type)
    }
}

var myCar = Car.init(color: "Black")
// result Black
```

# 2.可选属性类型 （Optional Property Types）
类型后面加 ? 为可选属性类型，它可以不必初始化(age)，否则必须在 init 方法中初始化
```swift
class Car {
    var age: String?
    var name: String
    
    init(color: String) {
        name = "sun"
        print(color)
    }
    
    init(type: String) {
        name = "sun"
        print(type)
    }
}
```
# 3.Designated and Convenience Initializers
Designated Initializers 是自定义的初始化函数（如:init(name: String)）,convenience Initializers必须调用本类内的Designated Initializers，遵循如下原则：
```swift
class Food {
    var name: String
    init(name: String) {
        print(2)
        self.name = name
    }
    convenience init() {
        print(3)
        self.init(name: "[Unnamed]")
    }
}

var food = Food() 
// result 3 2 
// 注：当类初始化的时候 convenience 会优先 Designated Initializers 执行
```
Rule 1
A designated initializer must call a designated initializer from its immediate superclass.

Rule 2
A convenience initializer must call another initializer from the same class.

Rule 3
A convenience initializer must ultimately call a designated initializer.
