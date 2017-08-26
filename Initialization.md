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
