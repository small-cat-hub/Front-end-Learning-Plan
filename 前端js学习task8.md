
# JavaScript 第二周：数据结构与函数进阶
(*11.15~11.21*)
## 🎯 学习目标
- 理解 JavaScript 中的数组与对象的核心操作  
- 掌握数组的高阶方法（map、filter、reduce 等）  
- 理解函数作为一等公民的概念（函数可以作为参数或返回值）  
- 理解闭包（Closure）与递归（Recursion）  
- 初步掌握 ES6 的解构赋值与扩展运算符  

---

## 📘 一、数组基础与常用操作

数组是 JavaScript 中最常用的数据结构之一，用于存储有序的数据集合。

### 1. 创建数组
```js
let arr1 = [1, 2, 3];
let arr2 = new Array(4, 5, 6);
console.log(arr1, arr2);
```

### 2. 访问与修改数组
```js
let fruits = ["apple", "banana", "cherry"];
console.log(fruits[0]); // apple
fruits[1] = "orange";
console.log(fruits); // ["apple", "orange", "cherry"]
```

### 3. 数组常用方法
| 方法 | 功能 |
|------|------|
| `push()` | 在末尾添加元素 |
| `pop()` | 删除最后一个元素 |
| `shift()` | 删除第一个元素 |
| `unshift()` | 在开头添加元素 |
| `indexOf()` | 查找元素下标 |
| `includes()` | 判断是否包含元素 |

```js
let nums = [1, 2, 3];
nums.push(4);
console.log(nums); // [1,2,3,4]
nums.pop();
console.log(nums); // [1,2,3]
```

---

## 📘 二、数组的高阶方法

### 1. forEach()
```js
let arr = [1, 2, 3];
arr.forEach(item => console.log(item * 2));
```

### 2. map()
```js
let doubled = arr.map(x => x * 2);
console.log(doubled); // [2, 4, 6]
```

### 3. filter()
```js
let even = arr.filter(x => x % 2 === 0);
console.log(even); // [2]
```

### 4. reduce()
```js
let sum = arr.reduce((acc, cur) => acc + cur, 0);
console.log(sum); // 6
```

---

## 📘 三、对象与结构化数据

### 1. 创建对象
```js
let person = {
  name: "Alice",
  age: 20,
  greet: function() {
    console.log("Hi, I'm " + this.name);
  }
};
person.greet();
```

### 2. 属性访问
```js
console.log(person.name);   // 点语法
console.log(person["age"]); // 方括号语法
```

### 3. 遍历对象
```js
for (let key in person) {
  console.log(key, person[key]);
}
```

---

## 📘 四、函数进阶：函数作为值

### 1. 函数作为参数
```js
function operate(a, b, fn) {
  return fn(a, b);
}

function add(x, y) { return x + y; }
function mul(x, y) { return x * y; }

console.log(operate(2, 3, add)); // 5
console.log(operate(2, 3, mul)); // 6
```

### 2. 函数返回函数
```js
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

let add5 = makeAdder(5);
console.log(add5(10)); // 15
```

---

## 📘 五、闭包与作用域链
```js
function counter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}

let c = counter();
console.log(c()); // 1
console.log(c()); // 2
console.log(c()); // 3
```

---

## 📘 六、递归（Recursion）
```js
function factorial(n) {
  if (n === 1) return 1;
  return n * factorial(n - 1);
}
console.log(factorial(5)); // 120
```

---

## 📘 七、解构赋值与扩展运算符
```js
let [a, b, c] = [1, 2, 3];
let { name, age } = { name: "Tom", age: 18 };
console.log(a, b, name);

let arr1 = [1, 2];
let arr2 = [...arr1, 3, 4];
console.log(arr2); // [1,2,3,4]
```

---

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
