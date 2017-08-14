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


