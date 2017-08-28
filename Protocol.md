# 1.示例:老师写了个协议让学生去执行
```swift
protocol SomeProtocol {
    func learnEnglish()
}

class Teacher {
    public var delegate: SomeProtocol?
}

class Student: SomeProtocol {
    func learnEnglish() {
        print("学习了英语!")
    }
}

var student = Student()

var teacher = Teacher()
teacher.delegate = student
teacher.delegate?.learnEnglish()
// result 学习了英语!
```
