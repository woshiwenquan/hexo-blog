---
title: Swift学习笔记之基本运算符
date: 2016-05-27 10:49:18
tags:
  - Swift
categories: Swift学习笔记
---

运算符是检查、改变、合并值的特殊符号或短语。Swift支持了大部分标准C语言的运算符，并且改进了很多特性来减少常规编码错误。例如(`=`)不放回值，以防止把想要判断相等运算符（`==`）的地方写成赋值符导致的错误。

## 赋值运算符

赋值运算（`a = b`），表示用`b`的值来初始化或更新`a`的值
``` Swift
let b = 1
var a = 2
a = b
//a 现在等于1
```

<!-- more -->

如果赋值运算符右边是一个多元组，它的元素马上被分解成多个常量或变量：
``` Swift
let (x, y) = (1, 2)
// 现在x等于1，y等于2
```
> 注：
* 与C语言和Objective－C不同，Swift的赋值操作并不返回任何值。所以一下代码是错误的
``` Swift
if a = b {
    //这句会报错，因为赋值运算符没有返回值
}
```
这个特性使得你无法把（`==`）错写成（`=`）,由于`if a = b`是错误代码，Swift能帮你避免此类错误的发生。

## 算术运算符

Swift 中所有数值类型都支持了基本的四则算术运算：
* 加法(`+`)
* 减法(`-`)
* 乘法(`*`)
* 除法(`/`)

> 注：
* 与C语言和objc不同的是，Swift默认情况下不允许在数值运算中出现溢出的情况。
* 加法运算符可以直接用于`String`字符串的拼接：
``` Swift
"Hello, "+"baby"//等于"Hello, baby"
```

## 求余运算符
求余运算符（`a % b`）是计算`b`的多少倍刚刚好可以容入`a`，返回多出来的那部分，就是余数。
> 注：
* 求余运算(`%`)在其它语言也叫做取模运算。然而严格来说，我们看该运算符对负数操作的结果，「求余」比「取模」更合适些。
* 在对负数`b`求余时，`b`的符号会被忽略。这意味着`a % b`和`a % -b`的结果是一样的。
* 不同于 C 语言和 objc，Swift 中是可以对浮点数进行求余的。
``` Swift
8 % 1.5      //等于0.5
2.5 % 1.5    //等于1
```

## 一元负号运算符
数值的正负号可以使用前缀 `-`（即一元负号）来切换：
``` Swift
let one = 1
let minusOne = -one        //minusOne等于-1
let plusOne = -minusOne    //plusOne等于1
```
> 注：
* 一元负号（`-`）写在操作数之前，中间没有空格。

## 一元正号运算符
一元正号（`+`）不做任何改变地返回操作数的值：
``` Swift
let minusSix = -6
let alsoMinusSix = +minusSix  // alsoMinusSix 等于 -6
```

## 组合赋值运算符
如同 C 语言，Swift 也提供把其他运算符和赋值运算（`=`）组合的组合赋值运算符，组合加运算（`+=`）是其中一个例子：
``` Swift
var a = 1
a += 2
// a 现在是 3
```
> 注：
* 组合赋值运算符没有返回值，`let b = a += 2`这类代码是错误的。

## 比较运算符
所有标准 C 语言中的比较运算都可以在 Swift 中使用：
* 等于（`==`）
* 不等于(`!=`)
* 大于(`>`)
* 小于(`<`)
* 大于等于(`>=`)
* 小于等于(`<=`)

当元组中的值可以比较时，你也可以使用这些运算符来比较它们的大小。例如，因为 `Int` 和 `String` 类型的值可以比较，所以类型为 `(Int, String)` 的元组也可以被比较。相反，`Bool` 不能被比较，也意味着存有布尔类型的元组不能被比较。

比较元组大小会按照从左到右、逐值比较的方式，直到发现有两个值不等时停止。如果所有的值都相等，那么这一对元组我们就称它们是相等的。例如：
``` Swift
(1, "zebra") < (2, "apple")   // true，因为 1 小于 2
(3, "apple") < (3, "bird")    // true，因为 3 等于 3，但是 apple 小于 bird
(4, "dog") == (4, "dog")      // true，因为 4 等于 4，dog 等于 dog
```

> 注：Swift 标准库只能比较七个以内元素的元组比较函数。如果你的元组元素超过七个时，你需要自己实现比较运算符。

## 三目运算符
三目运算符的特殊在于它是有三个操作数的运算符，它的形式是`question ? answer1 : answer2`。它简洁的表达了根据问题成立与否作出二选一的操作。如果`question`成立返回`answer1`的结果；否则返回`answer2`的结果。

三目运算符是以下代码的缩写形式：
``` Swift
if question {
    answer1
} else {
    answer2
}
```
> 三目运算提供有效率且便捷的方式来表达二选一的选择。需要注意的事，过度使用三目运算符会使简洁的代码变的难懂。我们应避免在一个组合语句中使用多个三目运算符。

## 空合运算符

空合运算符（`a ?? b`）将对可选类型 `a` 进行空判断，如果 `a` 包含一个值就进行解封，否则就返回一个默认值 `b`。表达式 `a` 必须是 Optional 类型。默认值 `b` 的类型必须要和 `a` 存储值的类型保持一致。

空合运算符是对以下代码的简短表达方法：

``` Swift
a != nil ? a! : b
```
> 如果 a 为非空值（non-nil），那么值 b 将不会被计算。这也就是所谓的短路求值。

## 区间运算符
Swift 提供了两个方便表达一个区间的值的运算符。

### 闭区间运算符
闭区间运算符（`a...b`）定义一个包含从 `a` 到 `b`（包括 `a` 和 `b`）的所有值的区间。`a` 的值不能超过 `b`。 ‌ 闭区间运算符在迭代一个区间的所有值时是非常有用的，如在 `for-in` 循环中：
``` Swift
for index in 1...5 {
    print("\(index) * 5 = \(index * 5)")
}
// 1 * 5 = 5
// 2 * 5 = 10
// 3 * 5 = 15
// 4 * 5 = 20
// 5 * 5 = 25
```

### 半开区间运算符

半开区间（`a..<b`）定义一个从 `a` 到 `b` 但不包括 `b` 的区间。 之所以称为半开区间，是因为该区间包含第一个值而不包括最后的值。

半开区间的实用性在于当你使用一个从 0 开始的列表（如数组）时，非常方便地从0数到列表的长度。

``` Swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("第 \(i + 1) 个人叫 \(names[i])")
}
// 第 1 个人叫 Anna
// 第 2 个人叫 Alex
// 第 3 个人叫 Brian
// 第 4 个人叫 Jack
```

## 逻辑运算符
逻辑运算的操作对象是逻辑布尔值。Swift 支持基于 C 语言的三个标准逻辑运算。
* 逻辑非（`!a`）
* 逻辑与（`a && b`）
* 逻辑或（`a || b`）

### 逻辑非
逻辑非运算（`!a`）对一个布尔值取反，使得 `true` 变 `false`，`false` 变 `true`。它是一个前置运算符，需紧跟在操作数之前，且不加空格。
``` Swift
let allowedEntry = false
if !allowedEntry {
    print("ACCESS DENIED")
}
// 输出 "ACCESS DENIED"
```

### 逻辑与

逻辑与（`a && b`）表达了只有 `a` 和 `b` 的值都为 `true` 时，整个表达式的值才会是 `true`。

只要任意一个值为 `false`，整个表达式的值就为 `false`。事实上，如果第一个值为 `false`，那么是不去计算第二个值的，因为它已经不可能影响整个表达式的结果了。

``` Swift
let enteredDoorCode = true
let passedRetinaScan = false
if enteredDoorCode && passedRetinaScan {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// 输出 "ACCESS DENIED"
```

### 逻辑或
逻辑或（`a || b`）是一个由两个连续的 `| `组成的中置运算符。它表示了两个逻辑表达式的其中一个为 `true`，整个表达式就为 `true`。

同逻辑与运算类似，逻辑或也是「短路计算」的，当左端的表达式为 `true` 时，将不计算右边的表达式了，因为它不可能改变整个表达式的值了。
``` Swift
let hasDoorKey = false
let knowsOverridePassword = true
if hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// 输出 "Welcome!"
```

### 逻辑运算符组合计算
我们可以组合多个逻辑运算来表达一个复合逻辑：
``` Swift
if enteredDoorCode && passedRetinaScan || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// 输出 "Welcome!"
```

> 注：
* Swift 逻辑操作符 `&&` 和 `||` 是左结合的，这意味着拥有多元逻辑操作符的复合表达式优先计算最左边的子表达式。
* 为了一个复杂表达式更容易读懂，在合适的地方使用括号来明确优先级是很有效的，虽然它并非必要的。

``` swift
if (enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// 输出 "Welcome!"
```