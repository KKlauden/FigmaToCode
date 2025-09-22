# 开发环境配置指南

## 📋 必需软件安装

### 1. 现代浏览器
**推荐：Google Chrome**
- [下载链接](https://www.google.com/chrome/)
- 为什么选择 Chrome：内置强大的开发者工具，最佳的调试体验

### 2. 代码编辑器
**推荐：Visual Studio Code**
- [下载链接](https://code.visualstudio.com/)
- 为什么选择 VS Code：丰富的插件生态，优秀的前端开发支持

### 3. Node.js 环境
**推荐版本：18.x 或更高**
- [下载链接](https://nodejs.org/)
- 选择 LTS 版本（长期支持版本）
- 验证安装：打开终端运行 `node --version` 和 `npm --version`

### 4. Git 版本控制
- **Windows/Mac**：[下载链接](https://git-scm.com/)
- **Mac 用户**：也可使用 `brew install git`
- 验证安装：终端运行 `git --version`

## 🔧 VS Code 插件配置

### 必装插件

1. **Live Server**
   - 功能：本地开发服务器，实时预览
   - 安装：在 VS Code 扩展商店搜索 "Live Server"

2. **Prettier - Code formatter**
   - 功能：代码自动格式化
   - 安装：搜索 "Prettier"

3. **Auto Rename Tag**
   - 功能：自动重命名 HTML 标签对
   - 安装：搜索 "Auto Rename Tag"

4. **CSS Peek**
   - 功能：快速查看 CSS 定义
   - 安装：搜索 "CSS Peek"

5. **Emmet**
   - 功能：快速编写 HTML/CSS（VS Code 内置）
   - 学习：[Emmet 语法](https://emmet.io/)

### 推荐插件

1. **Bracket Pair Colorizer 2**
   - 功能：括号配对着色

2. **indent-rainbow**
   - 功能：缩进可视化

3. **Color Highlight**
   - 功能：颜色值高亮显示

## 🎨 VS Code 配置优化

创建 `.vscode/settings.json` 文件：

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "editor.minimap.enabled": false,
  "workbench.colorTheme": "Dark+ (default dark)"
}
```

## 🤖 AI 工具配置

### Claude Code (推荐)
1. 访问 [claude.ai/code](https://claude.ai/code)
2. 注册 Anthropic 账号
3. 熟悉基本使用方法

### GitHub Copilot (可选)
1. 在 VS Code 中安装 GitHub Copilot 插件
2. 需要 GitHub Pro 账号或学生认证

## 📁 项目文件结构

推荐的项目文件夹结构：

```
my-learning-projects/
├── 01-html-css-basics/
│   ├── practice/
│   ├── projects/
│   └── notes/
├── 02-responsive-design/
├── 03-javascript-basics/
└── README.md
```

## 🌐 在线工具配置

### 1. CodePen
- [注册账号](https://codepen.io/)
- 用于快速原型和实验

### 2. GitHub
- [注册账号](https://github.com/)
- 用于代码托管和版本控制

### 3. Figma
- [注册账号](https://figma.com/)
- 获取设计稿和学习组件系统

## 🔍 浏览器开发者工具配置

### Chrome DevTools 基础设置

1. **打开方式**：
   - F12 或 Ctrl+Shift+I (Windows)
   - Cmd+Option+I (Mac)
   - 右键页面 → "检查"

2. **推荐面板布局**：
   - Elements：查看 HTML 结构
   - Console：JavaScript 调试
   - Sources：代码调试
   - Network：网络请求分析

3. **设备模拟**：
   - 点击设备图标切换到移动设备视图
   - 测试响应式设计

## ✅ 环境验证检查

完成安装后，请验证以下命令：

```bash
# 检查 Node.js
node --version
# 应显示：v18.x.x 或更高

# 检查 npm
npm --version
# 应显示：9.x.x 或更高

# 检查 Git
git --version
# 应显示：git version 2.x.x

# 创建测试项目
mkdir test-project
cd test-project
npm init -y
```

## 🚀 第一个项目测试

创建简单的 HTML 文件测试环境：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>环境测试</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
        }
        .success {
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <h1>🎉 恭喜！开发环境配置成功</h1>
    <div class="success">
        <h2>✅ 环境验证通过</h2>
        <p>你已经准备好开始学习前端开发了！</p>
    </div>
    <button onclick="celebrate()">点击庆祝一下</button>

    <script>
        function celebrate() {
            alert('🚀 准备开始你的前端学习之旅吧！');
        }
    </script>
</body>
</html>
```

保存为 `test.html`，在 VS Code 中右键选择 "Open with Live Server" 预览。

## 🆘 常见问题解决

### Node.js 安装问题
- **问题**：npm 命令无法识别
- **解决**：重启终端，或添加 Node.js 到系统 PATH

### VS Code 插件无法安装
- **问题**：插件安装失败
- **解决**：检查网络连接，或使用 VPN

### Live Server 无法启动
- **问题**：右键菜单没有 "Open with Live Server"
- **解决**：确认插件已安装并启用，重启 VS Code

### Git 权限问题
- **问题**：Git 推送被拒绝
- **解决**：配置 Git 用户信息：
```bash
git config --global user.name "你的姓名"
git config --global user.email "your.email@example.com"
```

## 📞 获取帮助

如果遇到配置问题：
1. 在课程仓库 [Issues](../../issues) 中搜索类似问题
2. 创建新的 Issue 描述具体问题
3. 向 AI 助手描述问题寻求解决方案

---

**配置完成后，你就可以开始 [模块 1](/modules/01-web-basics/) 的学习了！** 🎯