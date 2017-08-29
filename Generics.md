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
# 2.Associated Types
Associated Types可以使协议动态设置返回类型、参数等
```swift
protocol Container {
    associatedtype Item
    mutating func append(_ item: Item)
    var count: Int { get }
    subscript(i: Int) -> Item { get }
}

struct Stack<Element>: Container {
    var item: Element = "A" as! Element
    
    // conformance to the Container protocol
    mutating func append(_ item: Element) {
    }
    subscript(i: Int) -> Element {
        return item
    }
}
```
Element 可以是任何类型，在实现接口的时候动态的设置

