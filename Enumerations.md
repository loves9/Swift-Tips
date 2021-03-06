# 1.swift的枚举跟OC不同，它没有默认整型值
```swift
enum CompassPoint {
    case north
    case south
    case east
    case west
}
print(CompassPoint.east)   // result east
```
也可以这样声明
```swift
enum CompassPoint {
    case north, south, east, west
}
```
swift虽然没有默认值但是可以设置 (Implicitly Assigned Raw Values)
```swift
enum CompassPoint: Int {
    case north = 0, south, east, west
}
print(CompassPoint.south.rawValue)  // result 1
```
如果不指定 north = 0 默认从0开始

# 2.关联值（Associated Values）
枚举可以关联值
```swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
    case max(Int)
    case list(Array<Any>)
}

var productBarcode = Barcode.upc(8, 85909, 51226, 3)
productBarcode = .qrCode("ABCDEFGHIJKLMNOP")
switch productBarcode {
case .upc(let numberSystem, let manufacturer, let product, let check):
    print("UPC: \(numberSystem), \(manufacturer), \(product), \(check).")
case .qrCode(let productCode):
    print("QR code: \(productCode).")
default: break
}
// result ABCDEFGHIJKLMNOP
```

# 3.递归枚举（Recursive Enumerations）
```swift
enum ArithmeticExpression {
    case number(Int)
    indirect case addition(ArithmeticExpression, ArithmeticExpression)
    indirect case multiplication(ArithmeticExpression, ArithmeticExpression)
}

let five = ArithmeticExpression.number(5)
let four = ArithmeticExpression.number(4)
let sum = ArithmeticExpression.addition(five, four)
let product = ArithmeticExpression.multiplication(sum, ArithmeticExpression.number(2))

func evaluate(_ expression: ArithmeticExpression) -> Int {
    switch expression {
    case let .number(value):
        return value
    case let .addition(left, right):
        return evaluate(left) + evaluate(right)
    case let .multiplication(left, right):
        return evaluate(left) * evaluate(right)
    }
}
 
print(evaluate(product))
// Prints "18"
```
