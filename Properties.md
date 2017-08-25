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


