# 🎨 两周 CSS 系统学习计划（含答案案例）

> 作者：陆发燎  
> 目标：系统学习 CSS，理解核心概念与布局，完成两个实战项目。

---

## 📆 总览

| 周次 | Task 名称 | 目标 | 输出成果 |
|------|-------------|------|-----------|
| 第 1 周 | **Task 1：掌握 CSS 基础与盒模型布局** | 打好基础、理解盒模型与常规布局 | 个人简介卡片 |
| 第 2 周 | **Task 2：进阶布局与视觉效果设计** | 掌握现代布局、动画与响应式设计 | 响应式主页 |

---

## 🧩 Task 1：掌握 CSS 基础与盒模型布局（第 1 周）

### 🎯 学习目标
掌握 CSS 基础语法、选择器、文本样式、盒模型与基础布局。

---

### ✅ 输出项目：个人简介卡片

#### 💡 项目要求
- 含头像、姓名、简介、按钮  
- 使用盒模型（margin、padding、border）  
- 使用类选择器和 hover 效果  

#### 📄 示例代码

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>个人简介卡片</title>
<style>
  body {
    background-color: #f4f6f9;
    font-family: "Microsoft YaHei", sans-serif;
  }

  .card {
    width: 300px;
    margin: 100px auto;
    background-color: white;
    border-radius: 15px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    text-align: center;
    padding: 20px;
  }

  .avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin-top: 10px;
    object-fit: cover;
  }

  h2 {
    margin-top: 15px;
    color: #333;
  }

  p {
    color: #666;
    font-size: 14px;
    margin: 10px 0 20px;
  }

  .btn {
    display: inline-block;
    background-color: #4CAF50;
    color: white;
    padding: 8px 18px;
    border-radius: 5px;
    text-decoration: none;
    transition: background-color 0.3s;
  }

  .btn:hover {
    background-color: #45a049;
  }
</style>
</head>
<body>

<div class="card">
  <img src="https://picsum.photos/id/1011/600/400" class="avatar" alt="头像">
  <h2>陆发燎</h2>
  <p>前端学习者，对 HTML/CSS/JS 感兴趣，正在构建自己的异步考核平台。</p>
  <a href="#" class="btn">联系我</a>
</div>

</body>
</html>
```

# 🧭 Task 2：CSS 第二周 —— 进阶布局与视觉效果设计（整合版）

> 📅 时间：第 8 ~ 14 天  
> ✍️ 作者：陆发燎  
> 🎯 目标：掌握现代布局（Flex、Grid）、动画、响应式与 CSS 变量，完成一个“响应式主页”项目。

---

## 🎯 学习目标
1. 理解 **Flex** 与 **Grid** 的现代布局方式；  
2. 能够使用 **transition**、**transform** 制作动效；  
3. 掌握 **@media** 媒体查询实现响应式设计；  
4. 学会使用 **CSS变量** 管理主题颜色；  
5. 制作一个带有动画与适配功能的网页主页。

---

## ✅ 实战项目：响应式主页（整合 HTML + CSS）

以下是整合后的完整代码，可直接保存为一个文件：  
例如：`index.html`

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>响应式主页</title>
  <style>
    :root {
      --main-color: #007BFF;
      --text-color: #333;
    }

    body {
      margin: 0;
      font-family: "Microsoft YaHei", sans-serif;
      color: var(--text-color);
      background-color: #f9fafc;
    }

    /* 顶部导航栏 */
    header {
      background-color: var(--main-color);
      color: white;
      padding: 15px 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
    }

    header h1 {
      font-size: 22px;
      margin: 0;
    }

    nav a {
      color: white;
      text-decoration: none;
      margin-left: 20px;
      font-size: 16px;
      transition: opacity 0.3s;
    }

    nav a:hover {
      opacity: 0.7;
    }

    /* 主体内容区 */
    .content {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 30px;
    }

    .card {
      background-color: white;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      transition: transform 0.3s, box-shadow 0.3s;
      overflow: hidden;
    }

    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }

    .card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
    }

    .card h3 {
      color: var(--main-color);
      margin: 15px;
    }

    .card p {
      font-size: 14px;
      color: #666;
      margin: 0 15px 20px;
      line-height: 1.6;
    }

    /* 底部栏 */
    footer {
      text-align: center;
      padding: 15px;
      background-color: #f0f0f0;
      font-size: 14px;
      color: #555;
    }

    /* 响应式设计 */
    @media (max-width: 600px) {
      header {
        flex-direction: column;
        align-items: flex-start;
      }

      nav a {
        display: inline-block;
        margin: 8px 0;
      }

      .card p {
        font-size: 13px;
      }
    }
  </style>
</head>
<body>

  <!-- 顶部导航栏 -->
  <header>
    <h1>我的主页</h1>
    <nav>
      <a href="#">首页</a>
      <a href="#">关于</a>
      <a href="#">联系</a>
    </nav>
  </header>

  <!-- 主体内容区 -->
  <section class="content">
    <div class="card">
      <img src="https://picsum.photos/id/1015/600/400" alt="学习卡片">
      <h3>前端学习</h3>
      <p>学习 HTML、CSS、JavaScript，构建网页的结构与样式。</p>
    </div>

    <div class="card">
      <img src="https://picsum.photos/id/1005/600/400" alt="项目卡片">
      <h3>项目实战</h3>
      <p>实践异步考核平台，提升代码质量与评测自动化能力。</p>
    </div>

    <div class="card">
      <img src="https://picsum.photos/id/1020/600/400" alt="目标卡片">
      <h3>未来方向</h3>
      <p>继续学习 Vue / React 框架，迈向全栈开发之路。</p>
    </div>
  </section>

  <!-- 底部栏 -->
  <footer>
    © 2025 陆发燎 | 前端学习之路
  </footer>

</body>
</html>
```