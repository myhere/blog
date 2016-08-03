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
