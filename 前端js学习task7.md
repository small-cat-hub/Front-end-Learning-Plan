# JavaScript 第一周：基础语法与逻辑思维
(*时间为11.8~11.14*)
## 🎯 本周目标
- 掌握 JavaScript 基本语法与程序结构  
- 理解变量、数据类型与运算符的行为与隐式转换  
- 熟练使用条件、循环与函数来表达算法逻辑  
- 培养调试思路与基本的逻辑/问题拆解能力

---

## 📘 一、环境与运行方式
- 浏览器环境：在 HTML 中通过 `<script>` 标签运行。  
  - 内联脚本：`<script>/* code */</script>`  
  - 外部脚本：`<script src="app.js"></script>`  
  - 模块脚本：`<script type="module" src="app.js"></script>`（支持 `import` / `export`）
- Node.js 环境：用于运行服务器端或本地脚本，命令行运行 `node script.js`。

---

## 📘 二、基本语法与语句结构
### 1. 注释
```js
// 单行注释
/* 多行
注释 */
```

### 2. 语句与分号
- JS 会执行自动分号插入（ASI），但在某些场景（如返回语句换行）会产生坑，建议养成写分号的习惯。

### 3. 标识符与大小写敏感
- 变量、函数、类名等都是大小写敏感的：`myVar` ≠ `myvar`

---

## 📘 三、变量与作用域（详细）
### 1. 三种声明方式：`var` / `let` / `const`
- `var`：函数作用域（或全局），存在变量提升（hoisting），可重复声明。
- `let`：块级作用域（`{}`），无提升到可用状态前访问会抛出 `ReferenceError`（暂时性死区 TDZ）。
- `const`：块级常量，声明时必须赋值，绑定不可变（指针不可变，但引用类型内部可变）。

**示例：**
```js
function demo() {
  console.log(a); // undefined （var 被提升）
  var a = 1;
  // console.log(b); // ReferenceError（如果取消注释）
  let b = 2;
}
```

### 2. 作用域链与闭包基础
- 内部作用域能访问外部声明；外部无法访问内部。闭包是函数与其词法作用域的组合。

---

## 📘 四、数据类型与类型转换（详细）
### 1. 原始类型（Primitive）
- `Number`、`String`、`Boolean`、`null`、`undefined`、`Symbol`、`BigInt`

### 2. 引用类型（Object）
- `Object`、`Array`、`Function`、`Date`、`RegExp` 等

### 3. `typeof` 与 `instanceof`
```js
typeof 123; // "number"
typeof null; // "object" （历史遗留）
[] instanceof Array; // true
```

### 4. 隐式转换与相等比较
- `==` 会进行类型转换，`===` 不会（推荐使用 `===`）
```js
0 == '0' // true
0 === '0' // false
null == undefined // true
```

### 5. 常见陷阱与建议
- 字符串与数字相加会发生拼接：`1 + '2' === '12'`  
- 对于金融计算避免使用 `Number` 浮点直接比较，考虑使用整数分（如以分为单位）或 BigInt/decimal 库。

---

## 📘 五、运算符详解（含优先级提示）
- 算术：`+ - * / % **`（指数）  
- 赋值：`=, +=, -=`  
- 比较：`==, ===, !=, !==, >, <, >=, <=`  
- 逻辑：`&&, ||, !`（短路特性）  
- 三元：`condition ? expr1 : expr2`

**注意短路赋值：**
```js
let a = null;
let b = a || 'default'; // 'default'（|| 返回第一个真值）
```

---

## 📘 六、控制流：条件与循环（含性能建议）
- 条件：`if / else if / else`、`switch`（适合离散值匹配）  
- 循环：`for`, `while`, `do...while`, `for...of`（遍历可迭代对象），`for...in`（遍历对象属性 — 不建议遍历数组）

**示例：使用 for...of 遍历数组**
```js
const arr = [10,20,30];
for (const v of arr) {
  console.log(v);
}
```

---

## 📘 七、函数详解（参数、this、提升）
### 1. 函数声明、函数表达式、箭头函数
```js
// 函数声明（有提升）
function add(a,b) { return a+b; }

// 函数表达式
const mul = function(a,b) { return a*b; }

// 箭头函数（无 this 绑定）
const sq = x => x*x;
```

### 2. 参数与默认值、剩余参数
```js
function fn(a=1, b=2, ...rest) { console.log(a,b,rest); }
fn(undefined, 5, 3,4); // 1 5 [3,4]
```

### 3. `this` 的四种绑定规则（简述）
- 默认绑定（全局/undefined 严格模式）  
- 隐式绑定（obj.method）  
- 显式绑定（call/apply/bind）  
- new 绑定（构造函数）  
箭头函数没有自己的 `this`，取决于定义时的外围作用域。

---

## 📘 八、调试技巧与常见错误排查
- 使用 `console.log/console.error/console.table` 输出调试信息。  
- 利用浏览器 DevTools：断点、条件断点、观察变量、查看调用堆栈（Call Stack）。  
- 常见错误：未定义变量、类型错误、异步顺序问题（注意 Promise / setTimeout）。

---

## 📘 九、逻辑思维训练（从题意到实现的步骤）
1. 理解题目与边界条件（输入类型、空集、极端值）  
2. 举例验证（手工模拟几个样例）  
3. 设计算法（选择合适的数据结构/循环）  
4. 编写代码并测试（单元测试/console 验证）  
5. 优化复杂度（时间/空间）

---

## 📆 每日学习计划（7 天）
| 天数 | 学习内容 |
|---|---|
| Day1 | 环境搭建、基本语法、注释、分号规则 |
| Day2 | 变量、作用域、var/let/const、作用域链 |
| Day3 | 数据类型、typeof、类型转换、相等比较 |
| Day4 | 运算符、表达式、短路、三元运算 |
| Day5 | 条件语句、循环、常见数组遍历方式 |
| Day6 | 函数（声明/表达式/箭头）、参数、this |
| Day7 | 调试技巧、逻辑训练、复习与练习 |

---

## 🧩 本周练习题（含答案）

### 练习 1 — 变量与作用域
```js
function test() {
  console.log(a);
  if (true) {
    var a = 1;
    let b = 2;
  }
  console.log(b);
}
test();
```
**结果分析：**
- `a` 输出 `undefined`（变量提升）  
- `b` 抛出 `ReferenceError`（块级作用域）  

**修正版：**
```js
function test() {
  var a;
  console.log(a); // undefined
  if (true) {
    a = 1;
    var b = 2;
  }
  console.log(b); // 2
}
test();
```

---

### 练习 2 — 类型与比较
```js
console.log(0 == '0'); 
console.log(0 === '0');
console.log(null == undefined);
console.log([] == 0);
```
**输出：**
```
true
false
true
true
```

---

### 练习 3 — 函数与 this
```js
const obj = {
  x: 10,
  getX: function() { return this.x; }
};
const get = obj.getX;
console.log(get());
```
**输出：** `undefined`  
**修正版：**
```js
const get = obj.getX.bind(obj);
console.log(get()); // 10
```

---

### 练习 4 — 数组去重
```js
function unique(arr) {
  const seen = new Set();
  const res = [];
  for (const x of arr) {
    if (!seen.has(x)) {
      seen.add(x);
      res.push(x);
    }
  }
  return res;
}
```

---

### 练习 5 — 判断质数
```js
function isPrime(n) {
  if (n <= 1) return false;
  if (n <= 3) return true;
  if (n % 2 === 0) return false;
  for (let i = 3; i <= Math.sqrt(n); i += 2) {
    if (n % i === 0) return false;
  }
  return true;
}
```

---

📚 **总结**
> 本周重点在于掌握 JavaScript 语言的核心基础：变量、类型、作用域、逻辑控制与函数。  
> 这些概念是后续学习 DOM、异步编程与 ES6 模块化的根基。
