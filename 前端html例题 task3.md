# HTML 基础知识与用法——练习题及答案

## 选择题

**1. 下列哪个标签用于定义网页的主标题？**
- A. `<p>`
- B. `<h1>`
- C. `<div>`
- D. `<span>`

**2. 关于 `<img>` 标签，哪个属性用于图片描述，提升无障碍和 SEO？**
- A. `src`
- B. `alt`
- C. `href`
- D. `title`

**3. 下面哪个标签是语义化标签，常用于网页的导航栏？**
- A. `<nav>`
- B. `<aside>`
- C. `<span>`
- D. `<table>`

**4. 如果想让链接在新窗口打开，应该使用哪个属性值？**
- A. `target="_self"`
- B. `target="_blank"`
- C. `target="_top"`
- D. `target="_parent"`

**5. 下列哪个标签可以实现无序列表？**
- A. `<ol>`
- B. `<ul>`
- C. `<dl>`
- D. `<li>`

---

## 填空题

**6. 使用实体字符让网页显示小于号，应写为 `______`。**

**7. HTML 注释的格式为：`______ 注释内容 ______`。**

**8. 在表单 `<form>` 中，输入框标签为 `______`，而提交按钮标签为 `______`。**

**9. 用于设置网页编码的标签是 `______`，常见取值为 `______`。**

**10. 让网页适配移动端设备的标签为：`<meta name="______" content="______">`。**

---

## 简答题

**11. 简述使用 `<div>` 和 `<span>` 的区别及适用场景。**

**12. 写一个包含标题、图片、列表和表单的简单 HTML 页面结构。**

---

## 答案

### 选择题答案
1. B
2. B
3. A
4. B
5. B

### 填空题答案
6. `&lt;`
7. `<!-- 注释内容 -->`
8. `<input>`，`<button>`
9. `<meta charset="...">`，`UTF-8`
10. `viewport`，`width=device-width, initial-scale=1.0`

### 简答题答案

**11.**
- `<div>` 是块级元素，用于布局、分区结构，能包含其他标签，也可配合样式实现复杂布局。
- `<span>` 是行内元素，适用于小范围文本或内联样式，不单独占一行。
- 一般结构分层用 `<div>`，局部样式或文本装饰用 `<span>`。

**12.**
```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="UTF-8">
    <title>练习页面</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
  <body>
    <h1>欢迎学习 HTML</h1>
    <img src="logo.png" alt="Logo" width="100">
    <ul>
      <li>HTML 基础</li>
      <li>CSS 样式</li>
      <li>JavaScript 交互</li>
    </ul>
    <form>
      <label for="name">姓名：</label>
      <input type="text" id="name" name="name">
      <button type="submit">提交</button>
    </form>
  </body>
</html>
```