# 第 4 周：DOM 操作与事件交互（含练习题与答案）
(*11.29~12.5*)
## 🎯 学习目标
- 理解 DOM 的结构与节点类型
- 掌握常用 DOM 操作（查找、修改、创建、删除）
- 学会使用事件监听器（addEventListener）
- 理解事件流（捕获、冒泡、委托）
- 掌握表单交互与动态网页更新

---

## 📅 每日学习计划

| 天数 | 学习主题 | 主要内容 |
|------|-----------|-----------|
| 第1天 | DOM 基础与节点结构 | 了解 DOM 树、节点类型、document 对象 |
| 第2天 | DOM 元素查找与选择 | getElementById、querySelector、querySelectorAll |
| 第3天 | DOM 操作与修改 | innerHTML、textContent、createElement、appendChild |
| 第4天 | 事件监听与绑定 | addEventListener、事件对象、this 指向 |
| 第5天 | 事件流与委托 | 捕获与冒泡机制、事件委托 |
| 第6天 | 表单操作与验证 | 获取输入值、表单验证、阻止默认事件 |
| 第7天 | 综合项目：交互式任务清单 | 练习 DOM + 事件综合应用 |

---

## 一、DOM 基础与节点结构

### 1. 什么是 DOM？
**DOM（Document Object Model）** 是浏览器将 HTML 文档转化成的对象模型，使 JavaScript 能够操作网页内容。

- HTML 文档会被解析为 **DOM 树结构**
- 每个 HTML 标签是一个 **节点（Node）**
- 节点包括：元素节点、文本节点、属性节点、注释节点

```html
<html>
  <body>
    <h1>Hello DOM</h1>
  </body>
</html>
```
DOM 树结构：

```
Document
 └── html
      └── body
           └── h1
                └── "Hello DOM"
```

### 2. 常用 DOM 属性
- `document.title`：获取/修改网页标题
- `document.body`：访问 `<body>` 元素
- `document.documentElement`：访问 `<html>` 根节点

---

## 二、DOM 元素查找与选择

### 1. 常用方法
```js
document.getElementById("id名")       // 返回单个元素
document.getElementsByClassName("类名") // 返回HTMLCollection
document.getElementsByTagName("标签名")
document.querySelector("选择器")        // 返回第一个匹配
document.querySelectorAll("选择器")     // 返回所有匹配
```

### 2. 示例
```html
<p id="text">Hello</p>
<script>
  const p = document.getElementById("text");
  console.log(p.textContent); // 输出 Hello
</script>
```

---

## 三、DOM 操作与修改

### 1. 修改内容
```js
element.innerHTML = "<b>新内容</b>";
element.textContent = "纯文本内容";
```

### 2. 修改样式
```js
element.style.color = "red";
element.style.backgroundColor = "yellow";
```

### 3. 创建与删除节点
```js
const div = document.createElement("div");
div.textContent = "新建的div";
document.body.appendChild(div);

document.body.removeChild(div);
```

---

## 四、事件监听与绑定

### 1. 三种绑定方式
```html
<!-- 内联绑定 -->
<button onclick="alert('点击了按钮')">点击</button>

<!-- DOM 属性绑定 -->
<script>
  btn.onclick = function() { alert("被点击！"); }
</script>

<!-- 推荐：addEventListener -->
<script>
  btn.addEventListener("click", () => alert("点击事件"));
</script>
```

### 2. 事件对象
```js
element.addEventListener("click", function(event){
  console.log(event.type); // click
  console.log(event.target); // 被点击的元素
});
```

---

## 五、事件流与事件委托

### 1. 事件流阶段
- 捕获阶段（从外到内）
- 目标阶段（到达目标）
- 冒泡阶段（从内到外）

```js
parent.addEventListener("click", () => console.log("父元素"), true);
child.addEventListener("click", () => console.log("子元素"), false);
```

### 2. 事件委托
在父元素上绑定事件，通过 `event.target` 判断触发的子元素。

```js
document.querySelector("#list").addEventListener("click", e => {
  if(e.target.tagName === "LI"){
    alert("你点击了 " + e.target.textContent);
  }
});
```

---

## 六、表单操作与验证

```html
<form id="loginForm">
  <input type="text" id="username" placeholder="用户名" required>
  <input type="password" id="password" placeholder="密码" required>
  <button type="submit">提交</button>
</form>

<script>
document.getElementById("loginForm").addEventListener("submit", e => {
  e.preventDefault(); // 阻止默认刷新行为
  const username = document.getElementById("username").value;
  const password = document.getElementById("password").value;
  if(username && password){
    alert("登录成功");
  } else {
    alert("请填写完整信息");
  }
});
</script>
```

---

## 七、综合项目：交互式任务清单

功能：  
- 输入任务 → 添加到列表  
- 点击任务 → 标记完成  
- 点击删除按钮 → 移除任务

```html
<h2>任务清单</h2>
<input type="text" id="taskInput" placeholder="输入任务">
<button id="addBtn">添加</button>
<ul id="taskList"></ul>

<script>
const input = document.getElementById("taskInput");
const btn = document.getElementById("addBtn");
const list = document.getElementById("taskList");

btn.addEventListener("click", () => {
  if(input.value.trim() === "") return;
  const li = document.createElement("li");
  li.textContent = input.value;
  li.addEventListener("click", () => li.classList.toggle("done"));
  list.appendChild(li);
  input.value = "";
});
</script>
```

---

## 🧠 每周练习题

#### 题目 1：获取页面所有 `<p>` 标签的内容并打印
#### 题目 2：创建一个按钮，点击后随机改变背景颜色
#### 题目 3：制作一个输入框，实时显示输入的文字长度
#### 题目 4：给列表中的每个项绑定点击事件，点击后变红
#### 题目 5：综合题：实现一个“待办事项”网页

---

## ✅ 参考答案

### 答案 1
```js
const ps = document.querySelectorAll("p");
ps.forEach(p => console.log(p.textContent));
```

### 答案 2
```js
const btn = document.querySelector("button");
btn.addEventListener("click", () => {
  document.body.style.backgroundColor = "#" + Math.floor(Math.random()*16777215).toString(16);
});
```

### 答案 3
```html
<input type="text" id="txt">
<p id="len"></p>
<script>
txt.addEventListener("input", () => {
  len.textContent = "当前长度：" + txt.value.length;
});
</script>
```

### 答案 4
```js
document.querySelectorAll("li").forEach(li => {
  li.addEventListener("click", () => {
    li.style.color = "red";
  });
});
```

### 答案 5
参考“交互式任务清单”示例。
