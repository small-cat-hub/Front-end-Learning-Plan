# JavaScript 第二周：函数、作用域与数组
(*11.15~11.21*)
## 🎯 本周目标
- 深入理解函数的定义、调用方式和作用域机制  
- 掌握闭包（Closure）与执行上下文（Execution Context）概念  
- 熟悉数组的常用方法与遍历技巧  
- 学会使用高阶函数（map、filter、reduce）进行数据处理  

---

## 📘 一、函数进阶（详细讲解）

### 1. 函数声明与函数表达式
```js
// 声明式函数（有提升）
function add(a, b) {
  return a + b;
}

// 表达式函数（无提升）
const multiply = function(a, b) {
  return a * b;
};

// 箭头函数（this 指向外层）
const divide = (a, b) => a / b;
```

💡 **注意**：箭头函数没有 `this`、`arguments`、`super` 和 `new.target`。

---

### 2. 参数与默认值
```js
function greet(name = "Guest") {
  return `Hello, ${name}!`;
}
console.log(greet()); // Hello, Guest!
```

- 默认参数在函数定义阶段就绑定  
- 若显式传入 `undefined`，也会触发默认值

---

### 3. 剩余参数（Rest Parameters）与展开运算符（Spread）
```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3, 4)); // 10

const arr = [1, 2, 3];
console.log(Math.max(...arr)); // 3
```

---

### 4. 函数作用域与提升
- 函数声明会整体提升（Hoisting）  
- 函数表达式不会被提升

```js
sayHello();
function sayHello() {
  console.log("Hello!");
}

// ❌ 错误
// sayHi(); // TypeError
const sayHi = function() {
  console.log("Hi!");
};
```

---

### 5. 闭包（Closure）
闭包是**函数与其外部词法作用域的组合**。即使外部函数执行结束，内部函数依然可以访问其变量。

```js
function createCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```
🔹 闭包常用于：数据私有化、缓存、模块化编程。

---

## 📘 二、作用域与执行上下文

### 1. 作用域类型
- **全局作用域**：所有代码可访问的最外层作用域。  
- **函数作用域**：函数内部声明的变量只在函数内有效。  
- **块级作用域**：由 `{}` 创建，`let` 和 `const` 声明的变量受限其中。

### 2. 作用域链（Scope Chain）
当访问变量时，JS 会沿作用域链从内到外逐层查找。  
若最外层仍未找到，则抛出 `ReferenceError`。

```js
const a = 10;
function outer() {
  const b = 20;
  function inner() {
    const c = 30;
    console.log(a, b, c);
  }
  inner();
}
outer(); // 10 20 30
```

---

### 3. 执行上下文与调用栈
- 每次函数执行时都会创建一个新的“执行上下文”。  
- 执行上下文按调用顺序压入“调用栈（Call Stack）”。  
- 函数返回后，该上下文被弹出。

```js
function A() { console.log("A"); B(); }
function B() { console.log("B"); }
A(); // 输出顺序：A → B
```

---

## 📘 三、数组（Array）详解

### 1. 数组的创建方式
```js
const arr1 = [1, 2, 3];
const arr2 = new Array(4, 5, 6);
const arr3 = Array.of(7, 8, 9);
```

### 2. 常用属性与基本操作
```js
arr1.length; // 数组长度
arr1.push(4); // 添加到末尾
arr1.pop();   // 删除最后一项
arr1.unshift(0); // 添加到开头
arr1.shift();    // 删除第一项
```

### 3. 遍历方式（推荐使用 for...of 或数组方法）
```js
const nums = [10, 20, 30];

// for 循环
for (let i = 0; i < nums.length; i++) console.log(nums[i]);

// for...of
for (const n of nums) console.log(n);

// forEach 方法
nums.forEach(n => console.log(n));
```

---

## 📘 四、数组高阶函数（map / filter / reduce）

### 1. map：对每个元素执行回调并返回新数组
```js
const arr = [1, 2, 3];
const squared = arr.map(x => x ** 2);
console.log(squared); // [1, 4, 9]
```

### 2. filter：筛选满足条件的元素
```js
const nums = [1, 2, 3, 4, 5];
const even = nums.filter(n => n % 2 === 0);
console.log(even); // [2, 4]
```

### 3. reduce：累计计算（最强大的数组方法之一）
```js
const sum = [1, 2, 3, 4].reduce((acc, val) => acc + val, 0);
console.log(sum); // 10
```

### 4. 综合使用：统计出现次数
```js
const words = ['apple', 'banana', 'apple'];
const count = words.reduce((acc, w) => {
  acc[w] = (acc[w] || 0) + 1;
  return acc;
}, {});
console.log(count); // { apple: 2, banana: 1 }
```

---

## 📘 五、数组的常见陷阱与性能优化
1. 避免稀疏数组（索引不连续）。  
2. 尽量使用 `map`、`filter`、`reduce` 等函数式写法代替手动循环。  
3. `splice` 会改变原数组，`slice` 不会。  
4. 对大数组频繁操作时，可用生成器（Generator）或惰性计算方式。

---

## 📆 每日学习计划（7 天）
| 天数 | 学习内容 |
|---|---|
| Day1 | 函数声明与表达式、箭头函数 |
| Day2 | 参数、默认值、剩余与展开运算符 |
| Day3 | 作用域与作用域链 |
| Day4 | 执行上下文与闭包原理 |
| Day5 | 数组基础与常用方法 |
| Day6 | 高阶数组函数（map、filter、reduce） |
| Day7 | 综合练习与逻辑思维提升 |

---

## 🧩 本周练习题与答案

### 练习 1 — 闭包应用
**题目：** 创建一个计数器函数，每次调用返回递增的数字。
```js
function createCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
```
**答案：**
```js
const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

### 练习 2 — 数组求和（reduce）
```js
const arr = [10, 20, 30];
const total = arr.reduce((sum, n) => sum + n, 0);
console.log(total); // 60
```

---

### 练习 3 — 过滤奇数
```js
const nums = [1, 2, 3, 4, 5];
const odd = nums.filter(n => n % 2 !== 0);
console.log(odd); // [1, 3, 5]
```

---

### 练习 4 — map 实现平方数组
```js
const arr = [1, 2, 3];
const squares = arr.map(n => n * n);
console.log(squares); // [1, 4, 9]
```

---

### 练习 5 — 综合题：计算成绩平均值
```js
const scores = [80, 90, 70];
const avg = scores.reduce((sum, s) => sum + s, 0) / scores.length;
console.log(avg); // 80
```

---

📚 **总结**
> 本周核心在于理解函数、作用域与数组的工作机制。  
> 掌握这些内容后，你将能构建出具备清晰逻辑与数据处理能力的程序。
