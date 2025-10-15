# JavaScript 第三周：对象、内置对象与字符串操作
(*11.22~11.28*)
## 🎯 本周目标
- 掌握对象（Object）的基本结构与使用方式  
- 理解原型（Prototype）与引用类型的特性  
- 熟悉常见内置对象（Math、Date、JSON）的用法  
- 深入学习字符串（String）操作与模板字符串  

---

## 📘 一、对象基础（Object）

### 1. 对象的定义方式
```js
// 字面量创建
const person = {
  name: "Alice",
  age: 25,
  greet: function() {
    console.log(`Hi, I'm ${this.name}`);
  }
};

// 构造函数创建
const user = new Object();
user.id = 1001;
user.name = "Bob";

// Object.create()
const admin = Object.create(person);
admin.role = "admin";
```

### 2. 属性访问与修改
```js
console.log(person.name); // 点语法
console.log(person["age"]); // 中括号语法
person.email = "alice@example.com"; // 新增属性
delete person.age; // 删除属性
```

### 3. 对象遍历
```js
const obj = {a:1, b:2, c:3};

// for...in
for (const key in obj) console.log(key, obj[key]);

// Object.keys / Object.values / Object.entries
console.log(Object.keys(obj));   // ['a','b','c']
console.log(Object.values(obj)); // [1,2,3]
console.log(Object.entries(obj)); // [['a',1],['b',2],['c',3]]
```

---

## 📘 二、构造函数与原型（Prototype）

### 1. 构造函数（Constructor Function）
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
const p1 = new Person("Tom", 20);
```
- 使用 `new` 调用构造函数时：  
  1. 创建一个新对象  
  2. 绑定 `this` 到该对象  
  3. 自动返回这个对象  

### 2. 原型与原型链
```js
Person.prototype.sayHi = function() {
  console.log(`Hi, I'm ${this.name}`);
};
p1.sayHi(); // "Hi, I'm Tom"
```
🔹 JS 通过“原型链”实现继承，当访问对象属性时，会向上查找其原型。

---

## 📘 三、内置对象（Math、Date、JSON）

### 1. Math 对象（数学计算）
```js
console.log(Math.PI);
console.log(Math.round(4.6)); // 四舍五入
console.log(Math.floor(4.9)); // 向下取整
console.log(Math.random());   // 0~1 随机数
```

### 2. Date 对象（日期与时间）
```js
const now = new Date();
console.log(now.getFullYear(), now.getMonth()+1, now.getDate());
console.log(now.toLocaleString());

const future = new Date("2030-01-01");
const diff = future - now;
console.log(diff / (1000*60*60*24)); // 相差天数
```

### 3. JSON 对象（序列化与反序列化）
```js
const user = { name: "Alice", age: 25 };
const str = JSON.stringify(user);
console.log(str); // '{"name":"Alice","age":25}'

const obj = JSON.parse(str);
console.log(obj.name); // Alice
```

---

## 📘 四、字符串（String）操作

### 1. 创建与基本属性
```js
const str = "Hello World";
console.log(str.length); // 11
```

### 2. 常用方法
```js
str.toUpperCase(); // 'HELLO WORLD'
str.toLowerCase(); // 'hello world'
str.includes("Hello"); // true
str.startsWith("He"); // true
str.endsWith("ld"); // true
str.indexOf("o"); // 4
str.replace("World", "JS"); // 'Hello JS'
str.slice(0,5); // 'Hello'
```

### 3. 模板字符串（Template Literals）
```js
const name = "Alice";
const age = 25;
console.log(`My name is ${name}, and I'm ${age} years old.`);
```

### 4. 多行字符串与表达式
```js
const msg = `
Today is ${new Date().toLocaleDateString()}
The sum of 2 + 3 = ${2 + 3}
`;
console.log(msg);
```

---

## 📘 五、对象与字符串综合运用
### 示例：将对象数组格式化为字符串
```js
const students = [
  {name:"Tom", score:88},
  {name:"Jerry", score:92}
];
const result = students.map(s => `${s.name}: ${s.score}`).join("; ");
console.log(result); // Tom: 88; Jerry: 92
```

---

## 📆 每日学习计划（7 天）
| 天数 | 学习内容 |
|---|---|
| Day1 | 对象定义、属性操作 |
| Day2 | 对象遍历与构造函数 |
| Day3 | 原型与继承机制 |
| Day4 | Math 与 Date 对象 |
| Day5 | JSON 序列化与反序列化 |
| Day6 | 字符串操作与模板字符串 |
| Day7 | 综合练习与复习 |

---

## 🧩 本周练习题与答案

### 练习 1 — 对象属性遍历
```js
const obj = {a:1,b:2,c:3};
for (const key in obj) console.log(key, obj[key]);
```
**输出：**
```
a 1
b 2
c 3
```

---

### 练习 2 — 构造函数与原型
```js
function Animal(type) {
  this.type = type;
}
Animal.prototype.speak = function() {
  console.log(`${this.type} makes a sound.`);
};
const dog = new Animal("Dog");
dog.speak(); // Dog makes a sound.
```

---

### 练习 3 — Math 与随机数
```js
// 生成 1~10 的随机整数
const rand = Math.floor(Math.random() * 10) + 1;
console.log(rand);
```

---

### 练习 4 — JSON 转换
```js
const data = {id:101, name:"Alice"};
const str = JSON.stringify(data);
console.log(str);
console.log(JSON.parse(str).name);
```
**输出：**
```
{"id":101,"name":"Alice"}
Alice
```

---

### 练习 5 — 字符串模板练习
```js
const product = "Laptop";
const price = 5999;
console.log(`商品：${product}，价格：${price} 元`);
```
**输出：**
```
商品：Laptop，价格：5999 元
```

---

📚 **总结**
> 本周重点在于理解 JavaScript 的对象体系与内置对象使用。  
> 学会操作字符串、理解 JSON 数据结构，为后续 DOM 与异步编程打下基础。
