# JavaScript 第一周：基础与语法（含练习题与扩展任务答案）
(*时间为11.8~11.14*)
## 🎯 学习目标

-   理解 JavaScript 的作用与运行环境\
-   掌握变量、数据类型、运算符与控制流\
-   学会定义与调用函数，理解作用域与提升（Hoisting）\
-   掌握基础调试技巧与错误排查方法

------------------------------------------------------------------------

## 📘 一、JavaScript 简介

JavaScript 是一种解释型脚本语言，主要用于网页交互与动态功能，也可运行在
Node.js 环境中。

``` html
<!-- 在 HTML 中引入 JS 的三种方式 -->
<!-- 方式 1：内联 -->
<button onclick="alert('Hello!')">点击我</button>

<!-- 方式 2：内部脚本 -->
<script>
  console.log("这是内部脚本");
</script>

<!-- 方式 3：外部脚本 -->
<script src="app.js"></script>
```

------------------------------------------------------------------------

## 📘 二、变量与作用域

### 1. 声明方式

-   `var`：函数作用域，可重复声明，会被提升（Hoisting）\
-   `let`：块级作用域，不能重复声明\
-   `const`：常量，声明时必须赋值

``` js
var a = 10;
let b = 20;
const c = 30;
console.log(a, b, c);
```

### 2. 作用域与作用域链

``` js
let x = 10;
function test() {
  let x = 20;
  console.log(x); // 输出 20
}
test();
console.log(x);   // 输出 10
```

------------------------------------------------------------------------

## 📘 三、数据类型与类型转换

### 1. 基本类型（7种）

`Number`, `String`, `Boolean`, `null`, `undefined`, `Symbol`, `BigInt`

``` js
let n = 123;            // Number
let s = "hello";        // String
let flag = true;        // Boolean
let u;                  // undefined
let z = null;           // null
let sym = Symbol("id"); // Symbol
let big = 123n;         // BigInt
```

### 2. 引用类型

对象、数组、函数都是引用类型。

``` js
let obj = { name: "Tom", age: 18 };
let arr = [1, 2, 3];
let fn = function() { console.log("hello"); };
```

### 3. 类型转换

``` js
console.log(Number("123"));  // 123
console.log(String(456));    // "456"
console.log(Boolean(""));    // false
console.log(Boolean("ok"));  // true
```

------------------------------------------------------------------------

## 📘 四、运算符与表达式

-   算术运算符：`+ - * / % **`
-   比较运算符：`==`、`===`、`!=`、`!==`、`>`、`<`
-   逻辑运算符：`&&`、`||`、`!`
-   赋值运算符：`=`、`+=`、`-=`
-   三元运算符：`条件 ? 值1 : 值2`

``` js
let score = 80;
let result = score >= 60 ? "及格" : "不及格";
console.log(result);
```

------------------------------------------------------------------------

## 📘 五、控制流语句

### 1. 条件判断

``` js
let num = 10;
if (num > 0) {
  console.log("正数");
} else if (num < 0) {
  console.log("负数");
} else {
  console.log("零");
}
```

### 2. 循环语句

``` js
for (let i = 1; i <= 5; i++) {
  console.log("循环次数:", i);
}
```

### 3. while 循环

``` js
let count = 0;
while (count < 3) {
  console.log("count =", count);
  count++;
}
```

------------------------------------------------------------------------

## 📘 六、函数与 Hoisting

### 1. 函数声明与调用

``` js
function add(a, b) {
  return a + b;
}
console.log(add(3, 5)); // 8
```

### 2. 函数表达式与箭头函数

``` js
let square = function (x) {
  return x * x;
};

let cube = (x) => x * x * x;

console.log(square(2), cube(3));
```

### 3. 变量提升（Hoisting）

``` js
console.log(a); // undefined
var a = 5;

// let/const 不会被提升
// console.log(b); ❌ ReferenceError
let b = 10;
```

------------------------------------------------------------------------

## 📘 七、调试与错误排查

### 1. console 系列

``` js
console.log("普通日志");
console.warn("警告信息");
console.error("错误信息");
```

### 2. 浏览器调试工具

-   打开开发者工具（F12）
-   使用 **断点** 调试变量变化
-   查看 **Console** 与 **Network** 面板输出

------------------------------------------------------------------------

## 📆 每日学习计划

  天数    学习内容
  ------- ------------------------------------------
  Day 1   JS 简介与运行环境、`<script>` 的三种用法
  Day 2   变量声明与作用域
  Day 3   数据类型与类型转换
  Day 4   运算符与表达式
  Day 5   条件与循环语句
  Day 6   函数定义、作用域与 Hoisting
  Day 7   调试技巧与复习小测

------------------------------------------------------------------------

## 🧩 每周练习题

1.  写一个函数 `isEven(num)` 判断输入数字是否为偶数。\
2.  打印 1\~100 中所有能被 3 整除的数。\
3.  写一个函数 `sumArray(arr)` 计算数组中所有元素的和。\
4.  写一个示例演示 `var` 与 `let` 的作用域差异。\
5.  使用 `prompt()` 输入姓名，输出 "你好, \[name\]！" 的弹窗。

------------------------------------------------------------------------

## 💡 扩展任务（进阶挑战）

-   编写一个函数 `max(a,b,c)` 返回三个数中的最大值。\
-   了解浏览器控制台中如何调试函数执行顺序。\
-   试着写一个简单的猜数字小游戏，包含循环与条件判断。

------------------------------------------------------------------------

## ✅ 每周练习题答案

### 1. 判断是否为偶数

``` js
function isEven(num) {
  return num % 2 === 0;
}
console.log(isEven(4)); // true
```

### 2. 打印 1\~100 中能被 3 整除的数

``` js
for (let i = 1; i <= 100; i++) {
  if (i % 3 === 0) console.log(i);
}
```

### 3. 计算数组中所有元素的和

``` js
function sumArray(arr) {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
    sum += arr[i];
  }
  return sum;
}
console.log(sumArray([1, 2, 3, 4, 5])); // 15
```

### 4. 演示 var 与 let 的作用域差异

``` js
if (true) {
  var a = 10;
  let b = 20;
}
console.log(a); // ✅ 输出 10
// console.log(b); // ❌ ReferenceError: b is not defined
```

### 5. 使用 prompt 输出问候语

``` js
let name = prompt("请输入你的名字：");
alert("你好, " + name + "！");
```

------------------------------------------------------------------------

## 🌟 扩展任务答案

### 1. 求三个数的最大值

``` js
function max(a, b, c) {
  return Math.max(a, b, c);
}
console.log(max(3, 7, 5)); // 7
```

### 2. 控制台调试函数执行顺序

``` js
function step1() {
  console.log("步骤1");
  step2();
}
function step2() {
  console.log("步骤2");
  step3();
}
function step3() {
  console.log("步骤3");
}
step1();
```

> ✅ 在浏览器开发者工具中添加断点可观察执行顺序。

### 3. 猜数字小游戏

``` js
let target = Math.floor(Math.random() * 10) + 1;
let guess;
do {
  guess = Number(prompt("猜一个 1~10 的数字："));
  if (guess > target) {
    alert("太大了！");
  } else if (guess < target) {
    alert("太小了！");
  } else {
    alert("恭喜你，猜对了！");
  }
} while (guess !== target);
```

------------------------------------------------------------------------
