# 1.示例:老师教学生学英语
```swift
protocol SomeProtocol {
    func learnEnglish(time: Int)
}

class Teacher {
    public var delegate: SomeProtocol?
    
    let hanMeiMei = Student()
    
    init() {
        delegate = hanMeiMei
    }
    
    func teacherEnglish(time: Int) {
        delegate?.learnEnglish(time: time)
    }
    
}

class Student: SomeProtocol {
    func learnEnglish(time: Int) {
        print("学习了\(time)小时英语!")
    }   
}

let missCang = Teacher()
missCang.teacherEnglish(time: 5)

// result 学习了5小时英语!
```
