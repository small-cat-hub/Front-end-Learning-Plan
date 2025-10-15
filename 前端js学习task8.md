
# JavaScript 第二周（超详细版）：数据结构与函数进阶

(*11.15~11.21*)
---

## 🎯 本周学习目标
- 深入理解数组、对象、Map、Set 的工作原理与使用场景。
- 熟悉闭包、作用域链、递归等函数进阶概念。
- 掌握高阶函数和函数式编程思想。
- 提高编写可复用、模块化代码的能力。

---

## 一、数组（Array）—— 从基础到进阶

### 1. 数组的本质
JavaScript 中数组是一种特殊的对象（`typeof [] === 'object'`）。
它的键实际上是字符串形式的索引，且具有一个特殊的属性 `length` 表示数组长度。

数组的索引从 0 开始，超出当前长度时会自动扩展。

```js
let arr = [1, 2, 3];
arr[5] = 6;
console.log(arr.length); // 6
console.log(arr); // [1, 2, 3, empty × 2, 6]
```

### 2. 数组的常用操作方法
| 分类 | 方法 | 是否修改原数组 | 说明 |
|------|------|----------------|------|
| 增加/删除 | `push()`, `pop()`, `shift()`, `unshift()`, `splice()` | ✅ | 改变原数组 |
| 访问 | `slice()`, `concat()` | ❌ | 不修改原数组 |
| 查找 | `indexOf()`, `find()`, `includes()` | ❌ | |
| 遍历 | `forEach()`, `map()`, `filter()`, `reduce()` | ❌ | |
| 其他 | `sort()`, `reverse()` | ✅ | 改变原数组 |

#### 示例：
```js
const arr = [1, 2, 3, 4, 5];
const squares = arr.map(x => x * x);
console.log(squares); // [1, 4, 9, 16, 25]
```

### 3. reduce 的应用
`reduce()` 可将数组归约为单个值，如求和、计数、分组等：

```js
const nums = [1, 2, 3, 4];
const sum = nums.reduce((acc, cur) => acc + cur, 0);
console.log(sum); // 10
```

它还能实现复杂操作：

```js
const fruits = ['apple', 'banana', 'apple', 'orange'];
const count = fruits.reduce((acc, item) => {
  acc[item] = (acc[item] || 0) + 1;
  return acc;
}, {});
console.log(count); // { apple: 2, banana: 1, orange: 1 }
```

### 4. 深入理解数组复制与引用
```js
let a = [1, 2, 3];
let b = a; // 引用相同地址
b.push(4);
console.log(a); // [1, 2, 3, 4]
```

解决：
```js
let c = [...a]; // 浅拷贝
```

### 5. 性能提示
- 尽量使用不可变操作（如 `map`、`filter`）。
- 避免频繁使用 `splice`、`shift` 等修改原数组的方法。

---

## 二、对象（Object）—— 数据与引用的本质

### 1. 对象创建
```js
const person = { name: 'Tom', age: 18 };
const clone = Object.assign({}, person); // 浅拷贝
```

### 2. 深拷贝与浅拷贝区别
- 浅拷贝只复制一层。
- 深拷贝复制所有层级。

实现：
```js
const deepCopy = obj => JSON.parse(JSON.stringify(obj));
```

### 3. Object 常用方法
```js
Object.keys(obj);
Object.values(obj);
Object.entries(obj);
Object.assign(target, source);
```

---

## 三、Map 与 Set —— 新型数据结构

### 1. Set
存储唯一值：
```js
const s = new Set([1, 2, 2, 3]);
console.log([...s]); // [1, 2, 3]
```

### 2. Map
可用对象或函数作为键：
```js
const m = new Map();
const obj = { a: 1 };
m.set(obj, 'hello');
console.log(m.get(obj)); // hello
```

---

## 四、函数进阶：闭包与作用域

### 1. 闭包定义
闭包是函数与其词法作用域的组合。

```js
function outer() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

### 2. 作用域链
- 内部函数可访问外部函数变量。
- 外部函数不能访问内部变量。

### 3. 高阶函数
高阶函数是指接受函数作为参数或返回函数的函数。

```js
function isType(type) {
  return obj => Object.prototype.toString.call(obj) === `[object ${type}]`;
}
const isArray = isType("Array");
console.log(isArray([])); // true
```

---

## 五、递归与函数式思维

### 1. 递归的基本结构
```js
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}
```

### 2. 递归的典型用途
- 计算树状结构节点数
- 数组扁平化
- 深拷贝对象

```js
function flatten(arr) {
  return arr.reduce((acc, cur) => acc.concat(Array.isArray(cur) ? flatten(cur) : cur), []);
}
console.log(flatten([1, [2, [3, 4]], 5])); // [1,2,3,4,5]
```

---

## 六、ES6+ 新特性强化

### 解构赋值
```js
const { name, age } = { name: 'Tom', age: 20 };
```

### 扩展运算符
```js
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = { ...obj1, ...obj2 };
```

---

## 📘 每周练习题 + 答案
（此处完整保留上次生成的题目与答案部分）

## 📆 每日学习计划

| 天数 | 学习内容 |
|------|-----------|
| Day 1 | 数组创建与基本操作 |
| Day 2 | 数组高阶方法（map、filter、reduce） |
| Day 3 | 对象的属性访问与遍历 |
| Day 4 | 函数作为参数与返回值 |
| Day 5 | 闭包与作用域链 |
| Day 6 | 递归与解构赋值 |
| Day 7 | 总结复习与项目练习 |

---

## 🧩 每周练习题

* 写一个函数 doubleArray(arr)，将数组中每个元素乘以 2。

* 编写一个函数 findMax(arr)，返回数组中的最大值。

* 创建一个闭包函数 createCounter()，实现计数器功能。

* 使用 reduce() 计算 [1,2,3,4,5] 的和。

* 使用递归编写一个函数 sumTo(n)，返回从 1 加到 n 的结果。

## 🧩 每周练习题与答案

```js
function doubleArray(arr) {
  return arr.map(x => x * 2);
}
console.log(doubleArray([1,2,3])); // [2,4,6]

function findMax(arr) {
  return Math.max(...arr);
}
console.log(findMax([3,5,1,9])); // 9

function createCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
let c = createCounter();
console.log(c()); // 1
console.log(c()); // 2

let arr = [1,2,3,4,5];
let sum = arr.reduce((acc, val) => acc + val, 0);
console.log(sum); // 15

function sumTo(n) {
  if (n === 1) return 1;
  return n + sumTo(n - 1);
}
console.log(sumTo(5)); // 15
```

---

## 🌟 扩展任务与答案

### 1. 记忆化斐波那契函数
```js
function memoFib() {
  let cache = {};
  return function fib(n) {
    if (n <= 2) return 1;
    if (cache[n]) return cache[n];
    cache[n] = fib(n - 1) + fib(n - 2);
    return cache[n];
  };
}
let f = memoFib();
console.log(f(10)); // 55
```

### 2. 深拷贝对象
```js
function deepCopy(obj) {
  return JSON.parse(JSON.stringify(obj));
}
let user = { name: "Tom", info: { age: 20 } };
let newUser = deepCopy(user);
newUser.info.age = 30;
console.log(user.info.age); // 20
```

### 3. 多维数组扁平化
```js
function flatten(arr) {
  return arr.reduce((acc, val) => 
    Array.isArray(val) ? acc.concat(flatten(val)) : acc.concat(val), []);
}
console.log(flatten([1, [2, [3, 4]], 5])); // [1,2,3,4,5]
```
