---
title: swift 学习笔记二
---

## enum

### 定义

> 普通枚举类型

```swift
enum CompassPoint {
  case north
  case east
  case south
  case west
}
```

### associated values

> 有点像 c 中的 union，每个 case 可以存储数据

#### 定义

```swift
enum Operand {
  case Unary(String, Double -> Double)
  case Binary(String, (Double, Double) -> Double)
}

let plus = Operand.Binary("+") {
  a, b in
    return a + b
}
```


#### 获取 associated value

```swift
enum Operand {
    case Unary(String, Double -> Double)
    case Binary(String, (Double, Double) -> Double)
}

let plus = Operand.Binary("+") {
    a, b in
    return a + b
}

switch plus {
    case .Unary(let operand, let fn):
        print("\(operand): \(fn)")
    case let .Binary(operand, fn):
        print("\(operand): \(fn)")
}
```


#### raw values

- is
  - set to prepopulated values when first define the enumeration
  - all of the same type


```swift
enum ASCIIControlCharactor: Charactor {
  case tab = "\t"
  case lineFeed = "\n"
  case carriageReturn = "\r"
}
```

- implicity assigned raw values

```swift
enum Week: Int {
  case Monday = 1, Thuesday, Wednesday, Thursday, Friday, Saturday, Sunday
}
// case 递增 +1

enum CompassPoint: String {
  case north, east, south, west
}
// value 为 case name
```

- access raw value

```swift
print(CompassPoint.north.rawValue)

```

- initializing from a raw value

```swift
let day: Week? = Week(rawValue: 7)
```

### recursive enumerations

- indicate enumeration case by prefixing `indirect`


```swift
enum ArithmeticExpression {
  case number(Int)
  indirect case addition(ArithmeticExpression, ArithmeticExpression)
  indirect case mulitiplication(ArithmeticExpression, ArithmeticExpression)
}

// or

indirect enum ArithmeticExpression {
  case number(Int)
  case addition(ArithmeticExpression, ArithmeticExpression)
  case mulitiplication(ArithmeticExpression, ArithmeticExpression)
}
```


```swift
indirect enum ArithmeticExpression {
    case number(Int)

    case mulitiplication(ArithmeticExpression, ArithmeticExpression)
    case addition(ArithmeticExpression, ArithmeticExpression)
}

// (5 + 4) * 2

let five = ArithmeticExpression.number(5)
let four = ArithmeticExpression.number(4)
let add = ArithmeticExpression.addition(five, four)

let two = ArithmeticExpression.number(2)
let multi = ArithmeticExpression.mulitiplication(add, two)

func calculate(_ expression: ArithmeticExpression) -> Int {
    switch expression {
    case let .number(num):
        return num
    case let .addition(a, b):
        return calculate(a) + calculate(b)
    case let .mulitiplication(a, b):
        return calculate(a) * calculate(b)
    }
}

print(calculate(multi))
```
