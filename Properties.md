# 1.Lazy Stored Properties（懒加载）
用lazy标记，在用到这个属性的时候才会被加载
```swift
class DataImporter {
    var filename = "data.txt"
    
    init() {
        print(filename)
    }
}

class DataManager {
    lazy var importer = DataImporter()
    var data = [String](["1"])
}

let manager = DataManager()
print(manager.data) // ["1"]

// 在用到这个属性的时候才会加载
print(manager.importer) // ["1"]  data.txt
```
注：多线程操作懒加载的时候，不保证仅初始化一次

# 2.Read-Only Computed Properties (只读属性)
声明属性的时候只写get方法会默认成只读属性，如下volume
```swift
struct Cuboid {
    var width = 0.0, height = 0.0, depth = 0.0
    var volume: Double {
        return width * height * depth
    }
}
let fourByFiveByTwo = Cuboid(width: 4.0, height: 5.0, depth: 2.0)
print("the volume of fourByFiveByTwo is \(fourByFiveByTwo.volume)")
// result the volume of fourByFiveByTwo is 40.0
```
# 3.属性观察者 （Property Observers）
类似OC的KVO，willSet和didSet关键字监听属性值的变化，oldValue是默认关键字
```swift
class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newTotalSteps) {
            print("About to set totalSteps to \(newTotalSteps)") // newTotalSteps值为200 
        }
        didSet {
            if totalSteps > oldValue  {
                print("Added \(totalSteps - oldValue) steps") // totalSteps值为200 oldValue值为0
            }
        }
    }
}
let stepCounter = StepCounter()
stepCounter.totalSteps = 200
```
NOTE

If you pass a property that has observers to a function as an in-out parameter, the willSet and didSet observers are always called. This is because of the copy-in copy-out memory model for in-out parameters: The value is always written back to the property at the end of the function. For a detailed discussion of the behavior of in-out parameters.
