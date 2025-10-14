# HTML 知识点讲解与典型案例
（*第一周的学习任务，时间为10.18~10.24*）
## 一、HTML 基础结构说明

HTML 文档需包含文档类型声明和基本结构标签：

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="UTF-8">
    <title>我的第一个网页</title>
  </head>
  <body>
    <h1>欢迎来到我的网站</h1>
    <p>这是一个段落。</p>
  </body>
</html>
```
**讲解：**
- `<!DOCTYPE html>` 声明 HTML5 文档。
- `<head>` 区域放元数据，如标题、编码、引入 CSS/JS 等。
- `<body>` 区域是网页可见内容。

---

## 二、常用标签用法案例

### 1. 标题与段落

```html
<h1>主标题</h1>
<h2>副标题</h2>
<p>正文内容，支持换行。</p>
```
**讲解：**
- `<h1>` 到 `<h6>` 用于分级标题，利于结构化和 SEO。
- `<p>` 标签用于文本段落。

### 2. 超链接与图片

```html
<a href="https://www.baidu.com" target="_blank">访问百度</a>
<img src="avatar.jpg" alt="头像" width="80">
```
**讲解：**
- `<a>` 创建超链接，`target="_blank"` 新窗口打开。
- `<img>` 显示图片，`alt` 是图片说明（无障碍/SEO），`width` 控制宽度。

### 3. 列表

```html
<ul>
  <li>苹果</li>
  <li>香蕉</li>
</ul>
<ol>
  <li>步骤一</li>
  <li>步骤二</li>
</ol>
```
**讲解：**
- `<ul>` 创建无序列表，`<ol>` 有序列表。
- `<li>` 列表项。

### 4. 表格

```html
<table border="1">
  <tr>
    <th>姓名</th>
    <th>年龄</th>
  </tr>
  <tr>
    <td>张三</td>
    <td>21</td>
  </tr>
</table>
```
**讲解：**
- `<table>` 是表格容器。
- `<tr>` 行，`<th>` 表头，`<td>` 单元格。

### 5. 表单

```html
<form action="/login" method="post">
  <label for="user">用户名：</label>
  <input type="text" id="user" name="user">
  <br>
  <label for="pwd">密码：</label>
  <input type="password" id="pwd" name="pwd">
  <br>
  <button type="submit">登录</button>
</form>
```
**讲解：**
- `<form>` 表单容器，`action` 指定提交路径，`method` 提交方式。
- `<label>` 关联输入框（`for` 属性对应输入框的 `id`）。
- `<input>` 有多种类型（`text`, `password`, `number` 等）。
- `<button>` 表单按钮。

---

## 三、标签属性讲解

```html
<div id="main" class="container" style="color:blue;">内容</div>
```
**讲解：**
- `id` 唯一标识，可用 JS/CSS 操作。
- `class` 类名，便于样式复用。
- `style` 内联样式，直接编写 CSS。

---

## 四、语义化标签案例

```html
<header>
  <nav>
    <a href="/">首页</a>
    <a href="/about">关于</a>
  </nav>
</header>
<main>
  <article>
    <h2>新闻标题</h2>
    <p>新闻内容……</p>
  </article>
</main>
<footer>
  <p>&copy; 2025 我的公司</p>
</footer>
```
**讲解：**
- `<header>` 页眉，通常包含 logo、导航等。
- `<nav>` 导航区域。
- `<main>` 主要内容区域。
- `<article>` 文章或独立内容块。
- `<footer>` 页脚。

---

## 五、嵌入多媒体案例

```html
<video src="demo.mp4" controls width="300"></video>
<audio src="demo.mp3" controls></audio>
```
**讲解：**
- `<video>`、`<audio>` 标签可以直接播放视频/音频，`controls` 显示控制栏。

---

## 六、特殊字符实体案例

```html
<p>5 &lt; 10 &amp; 8 &gt; 3</p>
```
**讲解：**
- `&lt;` 表示小于号 `<`，`&gt;` 表示大于号 `>`，`&amp;` 表示`&`。

---

## 七、注释用法

```html
<!-- 这里是注释，页面不会显示 -->
```
**讲解：**
- 用于代码解释、提醒或结构说明，不会被浏览器渲染。

---

## 八、常见布局示例

### 两栏布局（使用 `<div>` 配合 CSS）

```html
<div style="display: flex;">
  <div style="flex:1; background:#eee;">左侧内容</div>
  <div style="flex:2; background:#ddd;">右侧内容</div>
</div>
```
**讲解：**
- 使用 `display: flex` 实现自适应两栏布局，便于响应式设计。

---

## 九、响应式设计基础

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
**讲解：**
- 让页面适配手机等不同屏幕，开发移动端网站必备。

---

## 十、综合案例

一个包含标题、图片、列表、表格、表单和语义化标签的页面：

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="UTF-8">
    <title>综合案例页面</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
  <body>
    <header>
      <h1>个人简介</h1>
      <img src="avatar.jpg" alt="头像" width="100">
    </header>
    <main>
      <section>
        <h2>兴趣爱好</h2>
        <ul>
          <li>编程</li>
          <li>阅读</li>
          <li>运动</li>
        </ul>
      </section>
      <section>
        <h2>成绩表</h2>
        <table border="1">
          <tr>
            <th>科目</th>
            <th>分数</th>
          </tr>
          <tr>
            <td>数学</td>
            <td>95</td>
          </tr>
        </table>
      </section>
      <section>
        <h2>联系我</h2>
        <form action="/contact" method="post">
          <label for="name">姓名：</label>
          <input type="text" id="name" name="name">
          <br>
          <label for="email">邮箱：</label>
          <input type="email" id="email" name="email">
          <br>
          <button type="submit">发送</button>
        </form>
      </section>
    </main>
    <footer>
      <p>&copy; 2025 我的个人网站</p>
    </footer>
  </body>
</html>
```
**讲解：**
- 集合了结构标签、语义化标签、内容标签、表格和表单，展示了一个完整网页的基本构成。

---

如需进一步深入某个知识点或案例，请继续提问！