---
layout: default
title: EP05：开发环境准备 - 配置基础开发工具
permalink: /modules/00-ai-setup/EP05-development-environment/
---

# EP05: 开发环境准备 - 配置基础开发工具 ⏱️ 20 分钟

## 🎯 这一步要完成什么

**快速配置基础开发环境**，为后续所有模块做好准备：

- 安装现代化终端 Warp ⚡
- 掌握必备的终端基础命令 💻
- 安装 Node.js + npm 环境 📦
- 安装 OpenAI Codex CLI 工具 🤖

**这 20 分钟将让你拥有完整的前端开发环境！** 🚀

## ⚡ 第一步：安装 Warp 终端（5 分钟）

### 什么是 Warp？

Warp 是一个现代化的终端应用，比系统默认终端更友好、更智能。简单理解：

- **系统终端** = 黑白的命令行界面
- **Warp** = 彩色、智能、用户友好的命令行界面

### 安装方法

#### macOS 用户

```bash
# 使用 Homebrew 安装（推荐）
brew install --cask warp
```

如果没有 Homebrew，直接去 [warp.dev](https://www.warp.dev/) 下载安装包。

#### Windows 用户

```powershell
# 使用 WinGet 安装
winget install Warp.Warp
```

或者直接去 [warp.dev](https://www.warp.dev/) 下载安装包。

### 验证安装

安装完成后：

1. 打开 Warp 应用
2. 你会看到一个现代化的终端界面
3. **暂时不用配置任何 AI 功能**，我们后续会用到

## 💻 第二步：终端基础命令（8 分钟）

### 设计师必备的 6 个命令

作为设计师，你只需要掌握这 6 个基础命令就足够了：

#### 1. `ls` - 查看当前文件夹内容

```bash
ls
# 显示当前文件夹里的所有文件和文件夹
```

#### 2. `cd` - 进入文件夹

```bash
cd Documents
# 进入 Documents 文件夹

cd Desktop/my-project
# 进入桌面的 my-project 文件夹
```

#### 3. `cd ..` - 返回上一级文件夹

```bash
cd ..
# 回到上一级文件夹
```

#### 4. `mkdir` - 创建新文件夹

```bash
mkdir my-website
# 创建一个名为 my-website 的文件夹
```

#### 5. `rm -rf` - 删除文件夹（谨慎使用！）

```bash
rm -rf old-project
# 删除 old-project 文件夹及其所有内容
# ⚠️ 注意：这个操作不可恢复！
```

#### 6. `code .` - 用 VS Code 打开当前文件夹

```bash
code .
# 在 VS Code 中打开当前文件夹
# 这是连接终端和 VS Code 的桥梁
```

### 快速练习

在 Warp 中尝试这个流程：

```bash
# 1. 查看当前位置的文件
ls

# 2. 创建一个测试文件夹
mkdir test-folder

# 3. 进入测试文件夹
cd test-folder

# 4. 确认你在新文件夹里
ls

# 5. 返回上一级
cd ..

# 6. 删除测试文件夹
rm -rf test-folder
```

**🎯 重点理解**：终端就是用文字命令来操作文件和文件夹，就像在 Finder/文件管理器中点击一样。

## 📦 第三步：安装 Node.js + npm（5 分钟）

### 什么是 Node.js 和 npm？

- **Node.js** = 让 JavaScript 能在电脑上运行的环境（不只是浏览器）
- **npm** = JavaScript 的"软件商店"，用来安装各种开发工具

### 安装方法

#### 方法一：官网安装（推荐）

1. 访问 [nodejs.org](https://nodejs.org/)
2. 下载 **LTS 版本**（长期支持版本，更稳定）
3. 双击安装包，一路点击"下一步"
4. 安装完成

#### 方法二：包管理器安装

**macOS (Homebrew)：**

```bash
brew install node
```

**Windows (WinGet)：**

```powershell
winget install OpenJS.NodeJS
```

### 验证安装

在 Warp 中运行：

```bash
# 检查 Node.js 版本
node -v
# 应该显示类似：v20.x.x

# 检查 npm 版本
npm -v
# 应该显示类似：10.x.x
```

如果两个命令都显示版本号，说明安装成功！

## 🤖 第四步：安装 OpenAI Codex CLI（2 分钟）

### 什么是 Codex CLI？

OpenAI Codex CLI 是终端版的 AI 编程助手，它是 VS Code 扩展版的补充：

- **VS Code 扩展** = 在编辑器里的 AI 助手
- **Codex CLI** = 在终端里的 AI 助手

### 安装命令

在 Warp 中运行：

```bash
npm install -g @openai/codex
```

### 验证安装

```bash
# 检查 Codex CLI 是否安装成功
codex --version
# 应该显示版本信息
```

**📝 注意**：

- 我们暂时不配置 Codex CLI
- 不需要登录或设置 API 密钥
- 后续用到时会详细介绍使用方法

## ✅ 完成检查

- [ ] Warp 终端能正常打开并使用
- [ ] 能执行基础终端命令（`ls`, `cd`, `mkdir` 等）
- [ ] Node.js 安装成功（`node -v` 有输出）
- [ ] npm 安装成功（`npm -v` 有输出）
- [ ] Codex CLI 安装完成（`codex --version` 有输出）

## 🎯 总结

**恭喜！** 🎉 你现在拥有了：

✨ **现代化终端** - Warp，比默认终端更友好
💻 **基础命令技能** - 能用命令行操作文件和文件夹
📦 **Node.js 环境** - 前端开发的基础运行环境
🤖 **AI 工具** - 终端版的编程助手

**这些工具的价值**：

- **Warp** 让终端操作更直观
- **基础命令** 让你能与开发工具沟通
- **Node.js + npm** 是所有现代前端项目的基础
- **Codex CLI** 是你未来的 AI 编程伙伴

## 🚀 下一步

环境配置完成！现在你可以：

1. **继续模块 00**：回到 [模块 00 总览](../) 完成剩余内容
2. **开始实战**：进入 [模块 01](../../01-web-basics/) 开始第一个网站项目

---

**设计师的开发环境**：你刚刚配置的不只是工具，而是打开了设计师通往编程世界的大门。这些工具将陪伴你完成从设计师到全栈开发者的转型之旅。🎨→💻✨
