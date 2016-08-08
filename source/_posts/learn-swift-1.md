---
title: swift 学习笔记一
---

## 基础数据类型

- Int
- Float
- Double
- String
- Boolean
- Tuple
  ```swift
  var status = (404, "not found")

  var status = (code: 404, msg: "not found")

  print("\(status.code), \(status.msg)")
  ```

## Optional


- `?`
  ```swift
  var msg:String? = "hello swift"
  ```
  - `nil`
- unwrapping
  - `!`
- optional binding
  - used with `if` and `while`
  - unwrapping
  - `where`
- implicitly unwrapped optionals
  - `!`
  ```swift
  var msg:String! = "hello swift!"
  ```
  - “unwrapped automatically whenever it is used”


## Closure


### closure expression syntax

{(`parameters`) -> `return type` in 
    `statements`
}

```swift
let names = ["hello", "world"]

let sortedNames = names.sort({ (a: String, b: String) -> Bool in
    return a > b
})
```

- inferring type from context

```swift
let sortedNames = names.sort({ a, b in
    return a > b
})

print(sortedNames)
```

- Implicit Returns from Single-Expression Closures

```swift
let sortedNames = names.sort({ s1, s2 in s1 > s2 } )
```

- shorthand argument names

```swift
let sortedNames = names.sort({ $0 > $1})
```

- Operator Functions

```swift
let sortedNames = names.sort(isOrderedBefore: >)
```

- Trailing Closures

```swift
let sortedNames = names.sort { (a, b) -> Bool in
    return a > b
}

let sortedNames = names.sort {$0 > $1}
```
