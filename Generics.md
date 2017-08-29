# 1.泛型函数 （Generic Functions）
泛型函数可以传入任意类型的参数
```swift
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let temporaryA = a
    a = b
    b = temporaryA
}

var someInt = 1
var anotherInt = 107
swapTwoValues(&someInt, &anotherInt)
print(someInt, anotherInt) // result 107 1

var someString = "someString"
var anotherString = "anotherString"
swapTwoValues(&someString, &anotherString)
print(someInt, anotherInt)  // result anotherString someString
```

