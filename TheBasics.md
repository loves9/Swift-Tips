# 1.swift如何判断类型
```swift
var array = Array<String>.init()

if array is Array<Any> {
    print(true)
}else{
    print(false)
}
```

# 2.switch语句
switch不用写break,默认执行一个case
```swift
switch 1 {
case 1:
    print(0)
case 1:
    print(1)
default:
    print(2)
}
// result  0
```
如果你想让它继续执行，加上fallthrough
```swift
switch 1 {
case 1:
    print(0)
    fallthrough
case 1:
    print(1)
default:
    print(2)
}
// result  0 1
```
# 3.swift支持相同方法名（不同类中），但是参数个数一定不同
不支持完全相同的函数（方法名和参数个数完全相同）

# 4.Default Parameter Values
```swift
func someFunction(parameterWithoutDefault: Int, parameterWithDefault: Int = 12) {
    // If you omit the second argument when calling this function, then
    // the value of parameterWithDefault is 12 inside the function body.
}
someFunction(parameterWithoutDefault: 3, parameterWithDefault: 6) // parameterWithDefault is 6
someFunction(parameterWithoutDefault: 4) // parameterWithDefault is 12
```
# 5.In-Out Parameters
形参变实参，直接修改外部变量
```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}

var someInt = 3
var anotherInt = 107
swapTwoInts(&someInt, &anotherInt)
print("someInt is now \(someInt), and anotherInt is now \(anotherInt)")
// Prints "someInt is now 107, and anotherInt is now 3"
```
# 6.函数作为参数（Function Types as Parameter Types）
```swift
func addTwoInts(_ a: Int, _ b: Int) -> Int {
    return a + b
}

func printMathResult(_ mathFunction: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    print("Result: \(mathFunction(a, b))")
}
printMathResult(addTwoInts, 3, 5)
// Prints "Result: 8"
```
注:以函数为参数的参数类型要和出入的参数（函数）保持一致（参数类型、返回值类型）

也可以作为返回值
```swift
func stepForward(_ input: Int) -> Int {
    return input + 1
}
func stepBackward(_ input: Int) -> Int {
    return input - 1
}

func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    return backward ? stepBackward : stepForward
}
var currentValue = 3
let moveNearerToZero = chooseStepFunction(backward: currentValue > 0)
// moveNearerToZero now refers to the stepBackward() function
```

# 7.嵌套函数（Nested Functions）
```swift
func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    func stepForward(input: Int) -> Int { return input + 1 }
    func stepBackward(input: Int) -> Int { return input - 1 }
    return backward ? stepBackward : stepForward
}
var currentValue = -4
let moveNearerToZero = chooseStepFunction(backward: currentValue > 0)
// moveNearerToZero now refers to the nested stepForward() function
while currentValue != 0 {
    print("\(currentValue)... ")
    currentValue = moveNearerToZero(currentValue)
}
print("zero!")
// -4...
// -3...
// -2...
// -1...
// zero!
```
