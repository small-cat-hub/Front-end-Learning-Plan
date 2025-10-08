# VSCode 前端开发使用教程与插件推荐

## 一、VSCode 简介

Visual Studio Code（简称 VSCode）是一款由微软开发的免费、开源、高效的轻量级代码编辑器。它支持多种语言，拥有丰富的插件生态，是前端开发的首选工具之一。

## 二、VSCode 安装

1. 访问官网：[https://code.visualstudio.com/](https://code.visualstudio.com/)
2. 选择对应操作系统下载安装包（Windows/Mac/Linux）。
3. 安装完成后打开 VSCode。

## 三、基本设置推荐

1. **中文语言包**  
   - 打开扩展商店（左侧活动栏中的方块图标）。
   - 搜索 `Chinese (Simplified) Language Pack for Visual Studio Code`，安装后，VSCode界面会切换为中文。

2. **字体与主题**  
   - 推荐字体：`Fira Code`、`JetBrains Mono`（支持代码连字）。
   - 更换主题：扩展商店搜索 `One Dark Pro`、`Dracula Official` 等流行主题。

3. **快捷键**  
   - 常用快捷键可参考官方文档：[VSCode 快捷键大全](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

## 四、前端常用插件推荐与说明

| 插件名称 | 作用 | 推荐理由 | 安装方式 |
| :--- | :--- | :--- | :--- |
| ESLint | 语法检测与格式化 | 保证代码规范，团队协作利器 | 搜索 `ESLint` |
| Prettier | 代码自动格式化 | 保持代码风格一致，自动修复格式 | 搜索 `Prettier - Code formatter` |
| Live Server | 本地服务器，自动刷新 | 开发 HTML/CSS/JS 时自动预览 | 搜索 `Live Server` |
| Path Intellisense | 路径自动补全 | 引入文件路径时智能补全 | 搜索 `Path Intellisense` |
| Auto Rename Tag | 自动同步修改标签 | 修改 HTML/XML 标签时自动同步闭合标签 | 搜索 `Auto Rename Tag` |
| Bracket Pair Colorizer 2 | 括号配色 | 方便查看嵌套关系 | 搜索 `Bracket Pair Colorizer 2` |
| GitLens | Git 增强显示 | 代码版本溯源、作者显示 | 搜索 `GitLens — Git supercharged` |
| vscode-icons | 文件图标美化 | 让文件类型一目了然 | 搜索 `vscode-icons` |
| CSS Peek | CSS 跳转 | 直接跳转到 CSS 定义，提高效率 | 搜索 `CSS Peek` |
| IntelliSense for CSS class names | CSS类名智能提示 | 自动补全 HTML 中 class 名 | 搜索 `IntelliSense for CSS class names` |
| Import Cost | 显示依赖包大小 | 优化依赖，关注性能 | 搜索 `Import Cost` |
| JavaScript (ES6) code snippets | JS代码片段 | 快速插入常用代码 | 搜索 `JavaScript (ES6) code snippets` |
| HTML CSS Support | HTML 中 CSS 智能提示 | 提高开发效率 | 搜索 `HTML CSS Support` |

> 更多插件可根据项目需求自行探索。

## 五、插件安装方法

1. 点击左侧“扩展”按钮（或使用快捷键`Ctrl+Shift+X`）。
2. 在搜索框输入插件名称。
3. 点击“安装”按钮完成安装。

## 六、前端开发常用配置（settings.json 示例）

```json
{
  "editor.fontFamily": "Fira Code, JetBrains Mono, Consolas, 'Courier New', monospace",
  "editor.fontLigatures": true,
  "editor.formatOnSave": true,
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "editor.tabSize": 2,
  "editor.renderWhitespace": "all",
  "prettier.singleQuote": true,
  "prettier.semi": true,
  "eslint.enable": true
}
```

上述配置可在“首选项”->“设置”->右上角“打开 settings.json”进行修改。

## 七、常见问题解决

- **插件未生效**：确认插件已启用，重启 VSCode。
- **格式化冲突**：如 ESLint 和 Prettier 存在冲突，可通过 `.eslintrc` 或 `.prettierrc` 文件配置规则。
- **Live Server 无法启动**：关闭占用端口的进程，或更换端口。

## 八、推荐学习资源

- [VSCode 官方文档](https://code.visualstudio.com/docs)
- [VSCode 快捷键大全](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [前端插件推荐合集](https://www.zhihu.com/question/41582576)

---

如有更具体的前端框架需求（如 React、Vue、Angular），可进一步安装对应插件（如 `Vetur`、`Vue 3 Snippets`、`Reactjs code snippets` 等），并根据项目类型进行个性化配置。