# 第 5 周：ES6 + 本地存储 + 综合项目（含练习题与答案）
(*12.6~12.12*)
## 🎯 学习目标
- 掌握 ES6 常用语法（解构、箭头函数、模块化、类）
- 理解并使用本地存储（localStorage / sessionStorage）
- 学会封装模块化代码
- 完成一个综合项目：任务管理系统

---

## 📅 每日学习计划

| 天数 | 学习主题 | 主要内容 |
|------|-----------|-----------|
| 第1天 | ES6 变量与解构赋值 | let / const / 模板字符串 / 数组与对象解构 |
| 第2天 | 箭头函数与函数优化 | 箭头函数语法、this 指向、默认参数 |
| 第3天 | 对象增强与类（Class） | 简写属性、方法定义、类与继承 |
| 第4天 | 模块化与导入导出 | export / import、模块作用域 |
| 第5天 | 本地存储 | localStorage 与 sessionStorage 的使用 |
| 第6天 | 综合项目设计 | 任务管理系统：功能规划与数据结构 |
| 第7天 | 综合项目实现 | 使用 ES6 + localStorage 完成项目 |

---

## 一、ES6 基础语法与解构赋值

### 1. let / const
```js
let a = 10;
const PI = 3.14;
```
- `let` 是块级作用域，不能重复声明  
- `const` 声明常量，必须初始化

### 2. 模板字符串
```js
let name = "小明";
console.log(`你好，${name}！`);
```

### 3. 解构赋值
```js
const [x, y] = [1, 2];
const {name, age} = {name: "张三", age: 18};
```

---

## 二、箭头函数与函数优化

### 1. 基本语法
```js
const sum = (a, b) => a + b;
```

### 2. 特点
- 不绑定自己的 `this`，继承外层作用域
- 可用于回调函数简写

```js
setTimeout(() => console.log("Hello ES6"), 1000);
```

### 3. 默认参数
```js
function greet(name = "游客") {
  console.log("你好，" + name);
}
greet();
```

---

## 三、对象增强与类（Class）

### 1. 属性与方法简写
```js
let name = "Tom";
let person = {
  name,
  sayHi() { console.log("Hi!"); }
};
```

### 2. 类与继承
```js
class Animal {
  constructor(name) { this.name = name; }
  speak() { console.log(this.name + " 发出声音"); }
}

class Dog extends Animal {
  speak() { console.log(this.name + " 汪汪叫"); }
}

const d = new Dog("小狗");
d.speak();
```

---

## 四、模块化开发

### 1. 导出与导入
```js
// utils.js
export function add(a, b) { return a + b; }

// main.js
import { add } from "./utils.js";
console.log(add(2, 3));
```

### 2. 默认导出
```js
// config.js
export default { version: "1.0" };

// main.js
import config from "./config.js";
```

---

## 五、本地存储（Web Storage）

### 1. localStorage
```js
localStorage.setItem("name", "小红");
console.log(localStorage.getItem("name")); // 小红
localStorage.removeItem("name");
localStorage.clear();
```

### 2. sessionStorage
- 存储在浏览器会话中，关闭页面即清除

```js
sessionStorage.setItem("token", "abc123");
```

### 3. JSON 存取复杂数据
```js
const user = { name: "小李", age: 20 };
localStorage.setItem("user", JSON.stringify(user));
console.log(JSON.parse(localStorage.getItem("user")).name);
```

---

## 六、综合项目：任务管理系统

### 🧩 功能需求
- 添加、删除、标记任务  
- 任务数据自动保存到 localStorage  
- 页面刷新后数据不丢失

### 💻 示例代码
```html
<h2>任务管理系统</h2>
<input id="taskInput" placeholder="输入任务">
<button id="addBtn">添加</button>
<ul id="taskList"></ul>

<script>
const input = document.getElementById("taskInput");
const btn = document.getElementById("addBtn");
const list = document.getElementById("taskList");

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function render() {
  list.innerHTML = "";
  tasks.forEach((t, i) => {
    const li = document.createElement("li");
    li.textContent = t.text;
    li.className = t.done ? "done" : "";
    li.addEventListener("click", () => toggle(i));
    list.appendChild(li);
  });
}

function toggle(i){
  tasks[i].done = !tasks[i].done;
  save();
}

function save(){
  localStorage.setItem("tasks", JSON.stringify(tasks));
  render();
}

btn.addEventListener("click", () => {
  if(input.value.trim() === "") return;
  tasks.push({text: input.value, done: false});
  input.value = "";
  save();
});

render();
</script>
```

---

## 🧠 每周练习题

#### 题目 1：使用解构从对象中取出 name 和 age
#### 题目 2：使用箭头函数计算数组元素之和
#### 题目 3：创建一个类 Car，包含属性 brand 和方法 run()
#### 题目 4：使用 localStorage 存储用户输入的昵称并显示
#### 题目 5：综合题：制作一个带有本地存储功能的笔记本应用

---

## ✅ 参考答案

### 答案 1
```js
const person = {name: "张三", age: 18};
const {name, age} = person;
console.log(name, age);
```

### 答案 2
```js
const arr = [1, 2, 3, 4];
const sum = arr.reduce((a, b) => a + b);
console.log(sum);
```

### 答案 3
```js
class Car {
  constructor(brand){ this.brand = brand; }
  run(){ console.log(this.brand + " 正在行驶"); }
}
const c = new Car("特斯拉");
c.run();
```

### 答案 4
```html
<input id="nick" placeholder="输入昵称">
<button id="save">保存</button>
<p id="show"></p>

<script>
save.addEventListener("click", () => {
  localStorage.setItem("nick", nick.value);
  show.textContent = "欢迎，" + nick.value;
});
</script>
```

### 答案 5
参考“任务管理系统”示例。
