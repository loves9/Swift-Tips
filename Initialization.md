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
