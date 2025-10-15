
# JavaScript 第三周：DOM、事件与浏览器 API（详解版）
(*11.22~11.28*)
## 🎯 本周目标
- 理解 DOM 的概念与文档结构（节点类型、树形结构）
- 熟练掌握常用的 DOM 查询与操作方法（创建/插入/删除/替换）
- 深入理解事件机制（事件流、冒泡/捕获、委托）并掌握常见事件处理技巧
- 掌握表单处理、验证与常用浏览器 API（localStorage、history、fetch 简介）
- 能够独立实现交互式页面组件（例如可增删改的 TODO 列表）

---

## 一、DOM（Document Object Model）基础 —— 深度讲解

### 1. 什么是 DOM
- DOM 是文档对象模型，将 HTML 文档表示为节点树（Tree of Nodes）。浏览器解析 HTML 后生成 DOM 树，JS 可以通过 DOM 操作页面结构和样式。

### 2. 节点类型与常见术语
- 元素节点（Element）: HTML 标签对应的节点，如 `<div>`、`<p>`。  
- 文本节点（Text）: 元素内部的文本。  
- 属性节点（Attribute）: 元素的属性（一般通过 `element.getAttribute()` / `element.setAttribute()` 访问）。  
- 根节点（document.documentElement）和文档节点（document）。

### 3. DOM 树的基本操作接口
- 查询元素：`getElementById`, `getElementsByClassName`, `getElementsByTagName`, `querySelector`, `querySelectorAll`。  
  - `querySelector` 返回第一个匹配元素（CSS 选择器），`querySelectorAll` 返回静态 NodeList（可用 `forEach` 遍历）。
- 创建元素：`document.createElement('div')`，创建文本节点 `document.createTextNode('hello')`。
- 插入与移除：`appendChild`, `insertBefore`, `replaceChild`, `removeChild`。现在常用：`parent.append(child)`, `elem.remove()`。
- 修改属性与样式：`element.setAttribute('id','x')`, `element.classList.add('active')`, `element.style.color = 'red'`。建议用 `classList` 切换样式而不是直接修改 `style`，利于维护与响应式设计。

### 4. NodeList vs HTMLCollection vs Array
- `querySelectorAll` 返回 NodeList（可用 `forEach`），但不是数组。可用 `[...nodeList]` 转为数组。  
- `getElementsByClassName` 返回实时 HTMLCollection（DOM 变化时自动更新），`querySelectorAll` 返回静态集合。

### 5. 性能提示
- 减少频繁操作 DOM：最好先构建文档片段（`DocumentFragment`）或字符串拼接，再一次性插入。  
- 使用事件委托减少事件监听器数量，尤其是大量子元素场景。

---

## 二、事件系统（Event）—— 深入与实战

### 1. 事件基础概念
- 事件是用户或浏览器产生的交互信号（如点击、输入、提交等）。通过事件监听器处理事件。

### 2. 添加/移除事件监听
- `element.addEventListener('click', handler, options)`，支持第三个参数（options）：`capture`（捕获阶段）、`once`（只执行一次）、`passive`（用于滚动等性能优化，表示不会调用 `preventDefault`）。  
- 移除监听：`element.removeEventListener('click', handler)` —— 必须传入相同的 handler 引用。

### 3. 事件对象（Event）与常用属性/方法
- `event.target`：事件触发的真实元素（触发源）。  
- `event.currentTarget`：当前处理事件的元素（绑定监听的元素）。  
- `event.preventDefault()`：阻止默认行为（如表单提交、链接跳转）。  
- `event.stopPropagation()`：阻止事件继续向上（或向下）传播。

### 4. 事件流：捕获 → 目标 → 冒泡
- 捕获阶段（从 document 到目标元素）、目标阶段（触发元素）、冒泡阶段（从目标向上到 document）。  
- 默认多数事件在冒泡阶段触发监听（`addEventListener` 默认 `capture=false`）。

### 5. 事件委托（Event Delegation）
- 在父元素上添加一个事件监听，通过 `event.target` 判断并处理子元素事件。  
- 优点：减少监听器数量、自动支持动态添加的子元素。适用于列表、表格等结构。

#### 示例：事件委托用于 TODO 列表的删除按钮处理
```js
document.querySelector('#list').addEventListener('click', (e) => {
  if (e.target.matches('.delete-btn')) {
    const li = e.target.closest('li');
    li && li.remove();
  }
});
```

### 6. 常见错误与注意事项
- 在循环中直接在元素上绑定匿名函数导致无法移除监听。  
- 使用 `innerHTML` 插入字符串含有脚本或不做转义会有 XSS 风险。优先使用 `textContent` 设置文本。  
- 滥用 `stopPropagation()` 会影响第三方库或全局逻辑，慎用。

---

## 三、表单与验证（Forms & Validation）

### 1. 表单元素访问
- 获取表单元素：`const form = document.querySelector('form')`，访问表单字段：`form.elements['name']` 或 `form.querySelector('input[name=name]')`。

### 2. 表单提交控制
- 监听 `submit` 事件，`event.preventDefault()` 阻止默认提交，进行前端验证或 AJAX 提交。

```js
form.addEventListener('submit', (e) => {
  e.preventDefault();
  const data = new FormData(form);
  // 发送 fetch 请求或处理数据
});
```

### 3. HTML5 内建验证
- 使用 `required`, `type="email"`, `minlength`, `pattern` 等属性可以让浏览器自动进行一些基本验证。  
- 通过 `input.checkValidity()`、`form.reportValidity()` 能获得或显示验证结果。

### 4. 表单数据序列化
- `new FormData(form)` 获取键值对，可与 `fetch` 一起发送 `FormData`，也可用 `Object.fromEntries(formData)` 转为对象。

---

## 四、浏览器存储与常用 API（localStorage/sessionStorage, fetch 简介）

### 1. localStorage / sessionStorage
- `localStorage`：持久化（数据在关闭浏览器后仍然存在）。  
- `sessionStorage`：同一会话有效（窗口/标签页关闭后清空）。  
- 使用：`localStorage.setItem('key', JSON.stringify(value))`，读取：`JSON.parse(localStorage.getItem('key'))`。

⚠️ 不要把敏感信息（如密码、token）直接保存在 localStorage，存在 XSS 漏洞风险。

### 2. fetch API 简介（网络请求）
- `fetch(url, options)` 返回 Promise，常用于发起异步请求。

```js
fetch('/api/data', { method: 'GET' })
  .then(res => {
    if (!res.ok) throw new Error(res.statusText);
    return res.json();
  })
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

### 3. history / location 简介
- `history.pushState()` 可以在不刷新页面的情况下改变 URL（用于 SPA 路由）。  
- `location.href` 获取或设置当前 URL，会触发页面跳转。

---

## 五、实践示例：构建一个带本地存储的 TODO 应用（核心代码解析）

### HTML（简化）
```html
<form id="todo-form">
  <input name="text" placeholder="输入任务" required />
  <button type="submit">添加</button>
</form>
<ul id="todo-list"></ul>
```

### JS 核心逻辑（关键函数）
```js
const form = document.getElementById('todo-form');
const list = document.getElementById('todo-list');

function render(todos) {
  list.innerHTML = todos.map((t, i) => `<li data-i="${i}">
    <span>${t}</span>
    <button class="delete-btn">删除</button>
  </li>`).join('');
}

function load() {
  return JSON.parse(localStorage.getItem('todos') || '[]');
}

function save(todos) {
  localStorage.setItem('todos', JSON.stringify(todos));
}

form.addEventListener('submit', (e) => {
  e.preventDefault();
  const text = form.elements['text'].value.trim();
  if (!text) return;
  const todos = load();
  todos.push(text);
  save(todos);
  render(todos);
  form.reset();
});

list.addEventListener('click', (e) => {
  if (e.target.matches('.delete-btn')) {
    const li = e.target.closest('li');
    const i = Number(li.dataset.i);
    const todos = load();
    todos.splice(i, 1);
    save(todos);
    render(todos);
  }
});

// 初次渲染
render(load());
```

### 关键点解析
- 使用事件委托（在 `list` 上监听）来处理删除按钮，动态添加的项也能工作。  
- `localStorage` 作为简单持久化方案，适用于小型应用。

---

## 六、调试与性能优化

### 1. 开发者工具使用技巧
- Elements 面板查看 DOM 树，Console 查看错误与日志，Network 监控请求，Performance 分析渲染与 JS 执行。  
- 在 Sources 面板中设置断点（事件监听断点、XHR 断点），观察调用栈与变量。

### 2. 性能优化建议
- 减少重排（reflow）与重绘（repaint）：批量修改 DOM（使用 `DocumentFragment` 或隐藏元素再修改）。  
- 避免频繁读取会触发回流的属性（如 `offsetWidth`）与同时写读操作交错。  
- 使用 `requestAnimationFrame` 做动画更新。

---

## 📘 每日学习计划（7 天）

| 天数 | 学习内容 |
|------|----------|
| Day 1 | DOM 基础、节点类型、DOM 树概念、常用查询方法 |
| Day 2 | 创建/插入/删除节点，属性与样式修改，classList 使用 |
| Day 3 | 事件基础、addEventListener、事件对象、preventDefault |
| Day 4 | 事件流（捕获/冒泡）、事件委托、性能与最佳实践 |
| Day 5 | 表单处理、FormData、HTML5 验证 API |
| Day 6 | 本地存储（localStorage/sessionStorage）、fetch 简介 |
| Day 7 | 综合实战：实现 TODO 应用并优化性能与可访问性 |

---

## 🧩 每周练习题（按难度排列）

### 基础题
1. 写出三种查询 DOM 元素的方法并给出示例。  
2. 使用 `createElement` 创建一个 `<p>` 元素并插入到页面上。  
3. 说明 `event.target` 与 `event.currentTarget` 的区别。

### 应用题
4. 写一个函数 `toggleClass(selector, className)`，切换某一选择器目标元素的 class。  
5. 使用事件委托实现一个列表项点击高亮（父元素监听），并确保只会有一个高亮项。  
6. 使用 `FormData` 将表单数据转为对象并打印到控制台。

### 实战题
7. 完成一个简单的 TODO 应用（与上面示例逻辑相同，但要求每项可编辑文本并保存）。  
8. 使用 `fetch` 请求一个公共 API（可以是 `https://jsonplaceholder.typicode.com/todos/1`）并输出结果到页面。  
9. 实现一个防抖函数 `debounce(fn, wait)`，并在输入框的 `input` 事件上使用，避免频繁触发请求。

---

## 🧠 参考答案（含解析）

### 基础题答案

1. 三种查询方法示例：
```js
document.getElementById('app');
document.getElementsByClassName('item');
document.querySelector('.container > p');
```

2. 创建并插入 `<p>`：
```js
const p = document.createElement('p');
p.textContent = 'Hello DOM';
document.body.appendChild(p);
```

3. `event.target` 是触发事件的具体元素，`event.currentTarget` 是当前正在处理事件的元素（绑定监听的元素）。

---

### 应用题答案

4. `toggleClass` 实现：
```js
function toggleClass(selector, className) {
  const el = document.querySelector(selector);
  if (!el) return;
  el.classList.toggle(className);
}
```

5. 事件委托实现列表高亮：
```js
const list = document.getElementById('list');
list.addEventListener('click', (e) => {
  const item = e.target.closest('li');
  if (!item) return;
  // 移除其他高亮
  [...list.children].forEach(li => li.classList.remove('active'));
  item.classList.add('active');
});
```

6. 使用 FormData 转对象打印：
```js
const form = document.querySelector('form');
const fd = new FormData(form);
const obj = Object.fromEntries(fd.entries());
console.log(obj);
```

---

### 实战题答案（参考实现）

7. TODO 可编辑并保存（简化版）
```html
<ul id="todo-list"></ul>
<form id="todo-form"><input name="text" /><button>add</button></form>
```
```js
function render(todos) {
  const list = document.getElementById('todo-list');
  list.innerHTML = todos.map((t,i) => `
    <li data-i="${i}">
      <span contenteditable="true" class="text">${t}</span>
      <button class="save">保存</button>
      <button class="delete">删除</button>
    </li>`).join('');
}

document.getElementById('todo-list').addEventListener('click', (e) => {
  const li = e.target.closest('li');
  const i = Number(li.dataset.i);
  const todos = JSON.parse(localStorage.getItem('todos') || '[]');
  if (e.target.matches('.delete')) {
    todos.splice(i,1);
    localStorage.setItem('todos', JSON.stringify(todos));
    render(todos);
  } else if (e.target.matches('.save')) {
    const text = li.querySelector('.text').textContent.trim();
    todos[i] = text;
    localStorage.setItem('todos', JSON.stringify(todos));
    render(todos);
  }
});

// init
if (!localStorage.getItem('todos')) localStorage.setItem('todos', JSON.stringify([]));
render(JSON.parse(localStorage.getItem('todos')));
```

8. fetch 请求示例：
```js
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(res => res.json())
  .then(data => {
    document.getElementById('result').textContent = JSON.stringify(data, null, 2);
  });
```

9. debounce 实现：
```js
function debounce(fn, wait) {
  let timer = null;
  return function(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), wait);
  };
}

// 使用
const input = document.getElementById('search');
input.addEventListener('input', debounce((e) => {
  console.log('搜索：', e.target.value);
}, 300));
```

---

✅ 本周你应掌握：DOM 操作、事件系统、表单处理与基本浏览器 API 的使用；能实现常见交互功能并考虑性能与安全性。
