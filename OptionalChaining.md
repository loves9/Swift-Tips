Optional Chaining让开发者可以访问、使用不确定的属性、方法、下角标等
# 1.可选链会把任何类型置为nil，甚至是Int类型
```swift
class Person {
    var residence: Residence?
    var age: Int?
    
}

class Residence {
    var numberOfRooms = 1
}

print(Person().age) // result nil
```

# 2.什么时候应用可选链
记住"the potential to fail"，就是在有可能访问失败的情况下应用

# 3.Accessing Properties Through Optional Chaining
观察如下代码
```swift
func createAddress() -> Address {
    print("Function was called.")
    
    let someAddress = Address()
    someAddress.buildingNumber = "29"
    someAddress.street = "Acacia Road"
    
    return someAddress
}
john.residence?.address = createAddress() // result 无打印
```
代码中john.residence为nil，函数createAddress并没有被调用，也就是说当john.residence?为nil时，后面的代码不会执行
