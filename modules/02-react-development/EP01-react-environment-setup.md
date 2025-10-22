---
layout: default
title: EP01：React环境搭建 + 第一个组件
permalink: /modules/02-react-development/EP01-react-environment-setup/
---

# EP01: React 环境搭建 + 第一个组件 ⏱️ 40 分钟

**🎧 EP01 配套播客**：
**🎵 从 Figma 组件到 React 组件：设计师的代码化思维**

- [🎧 Internet Archive 收听](https://archive.org/details/02-ep-01-react-environment-setup) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/02-ep-01-react-environment) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**从静态 HTML 到动态 React 的第一步**：

- 搭建 Vite + React 19 现代化开发环境 🚀
- 理解 JSX 语法与 HTML 的区别和联系 📝
- 创建第一个 React 函数组件 ⚛️
- 体验"Figma 组件 →React 组件"的思维转换 🎨

**这 40 分钟将让你进入 React 开发的世界！** ✨

## 🛠 React 环境搭建：现代化开发体验（15 分钟）

### 第一步：安装 Node.js 和开发工具

1. **确认 Node.js 版本**

   ```bash
   node --version
   npm --version
   ```

   - 需要 Node.js 16+版本
   - 如果没有，前往 [nodejs.org](https://nodejs.org/) 下载 LTS 版本

2. **创建 React 项目**

   ```bash
   # 在桌面或你喜欢的位置创建项目
   npm create vite@latest my-react-website -- --template react
   cd my-react-website
   npm install
   ```

3. **启动开发服务器**
   ```bash
   npm run dev
   ```
   - 浏览器会自动打开 `http://localhost:5173`
   - 你会看到一个默认的 React 应用！

### 第二步：了解项目结构

```
my-react-website/
├── public/          # 静态文件
├── src/             # 源代码
│   ├── App.jsx      # 主应用组件
│   ├── main.jsx     # 应用入口
│   └── index.css    # 全局样式
├── package.json     # 项目配置
└── vite.config.js   # 开发环境配置
```

**核心理解**：

- `.jsx` 文件 = JavaScript + HTML 的组合
- `App.jsx` = 你的主要工作区域
- 保存文件后页面会自动刷新（热更新）

## ⚛️ 第一个 React 组件：从 HTML 到 JSX（10 分钟）

### 第一步：清理默认内容

打开 `src/App.jsx`，将内容替换为：

```jsx
function App() {
  return (
    <div className="App">
      <h1>我的React个人网站</h1>
      <p>欢迎来到React的世界！</p>
    </div>
  );
}

export default App;
```

**保存文件**，看看浏览器中的变化！🎉

### 第二步：理解 JSX 语法

**JSX vs HTML 的关键区别**：

| HTML                      | JSX                           | 说明                    |
| ------------------------- | ----------------------------- | ----------------------- |
| `<div class="container">` | `<div className="container">` | 用 className 替代 class |
| `<img src="..." />`       | `<img src="..." />`           | 自闭合标签必须有斜杠    |
| `<input type="text">`     | `<input type="text" />`       | 所有标签都要闭合        |

**核心理解**：

- JSX = JavaScript 中的 HTML 语法
- 看起来像 HTML，但有一些规则
- 必须要有一个根元素包裹所有内容

### 第三步：添加你的个人信息

```jsx
function App() {
  return (
    <div className="App">
      {/* 个人介绍区域 */}
      <header>
        <h1>张小明</h1>
        <h2>UI/UX 设计师</h2>
        <p>
          你好！我是一名专注于用户体验设计的UI设计师，现在正在学习React开发。
        </p>
      </header>

      {/* 技能列表 */}
      <section>
        <h3>我的技能</h3>
        <ul>
          <li>用户界面设计（UI Design）</li>
          <li>用户体验设计（UX Design）</li>
          <li>原型制作（Prototyping）</li>
          <li>React开发（学习中）</li>
        </ul>
      </section>
    </div>
  );
}

export default App;
```

**注意观察**：

- `{/* */}` = JSX 中的注释语法
- 结构和 HTML 很相似，但这是 JavaScript 代码！

## 🎨 设计师的 React 思维转换（10 分钟）

### Figma 组件 ↔ React 组件

**在 Figma 中**，你会这样工作：

1. 创建一个组件（比如按钮）
2. 定义组件的变体（不同状态）
3. 在页面中使用组件实例

**在 React 中**，概念完全一样：

1. 创建一个 React 组件（函数）
2. 定义组件的参数（Props）
3. 在页面中调用组件

### 创建你的第一个 React 组件

**将个人介绍提取为独立组件**：

在 `src` 文件夹中创建 `PersonalIntro.jsx`：

```jsx
function PersonalIntro() {
  return (
    <header>
      <h1>张小明</h1>
      <h2>UI/UX 设计师</h2>
      <p>你好！我是一名专注于用户体验设计的UI设计师，现在正在学习React开发。</p>
    </header>
  );
}

export default PersonalIntro;
```

**在 App.jsx 中使用这个组件**：

```jsx
import PersonalIntro from "./PersonalIntro";

function App() {
  return (
    <div className="App">
      {/* 使用你创建的组件 */}
      <PersonalIntro />

      {/* 技能列表 */}
      <section>
        <h3>我的技能</h3>
        <ul>
          <li>用户界面设计（UI Design）</li>
          <li>用户体验设计（UX Design）</li>
          <li>原型制作（Prototyping）</li>
          <li>React开发（学习中）</li>
        </ul>
      </section>
    </div>
  );
}

export default App;
```

**🎉 恭喜！** 你刚刚创建了第一个 React 组件！

## 🤖 AI 协作：React 开发助手（3 分钟）

### 基础代码转换

在 Codex 中尝试这些 React 转换：

1. **HTML 转 JSX**

   ```
   把这个HTML结构转换为React JSX：
   <div class="card">
     <img src="avatar.jpg" alt="头像">
     <h3>姓名</h3>
   </div>
   ```

2. **组件创建**

   ```
   创建一个React组件显示技能列表，包含：
   - 组件名：SkillList
   - 显示4个技能项目
   - 每个技能有图标和文字
   ```

3. **样式应用**
   ```
   在React组件中怎么应用CSS样式？
   className和style属性有什么区别？
   ```

### 理解 AI 的 React 建议

当你问 AI React 问题时，关注这些关键概念：

```
"我想创建一个卡片组件"
→ AI会建议创建函数组件，用JSX返回HTML结构

"怎么让组件可以配置内容？"
→ AI会建议使用Props参数

"如何组织多个组件？"
→ AI会建议组件拆分和import/export
```

## 🧠 设计师的 React 思维训练（2 分钟）

### React 组件 = 可复用的设计元素

**设计师常见疑惑**：

- ❓ "为什么要把 HTML 拆分成组件？"
- ❓ "组件和普通 HTML 有什么区别？"
- ❓ "什么时候需要创建新组件？"

**React 思维建立**：

- ✅ **组件 = 可复用的 UI 单元**（就像 Figma 中的组件）
- ✅ **每个组件都是独立的**（有自己的逻辑和样式）
- ✅ **组件可以组合**（小组件组成大组件）
- ✅ **组件可以配置**（通过参数改变显示内容）

### 快速 React 实验

在 Codex 中尝试这些快速实验：

1. **组件拆分**

   ```
   把我的网站拆分成这些React组件：
   - Header（导航）
   - PersonalIntro（个人介绍）
   - SkillList（技能列表）
   - Footer（页脚）
   ```

2. **组件复用**
   ```
   创建一个SkillItem组件，让我可以这样使用：
   <SkillItem name="UI设计" icon="🎨" />
   <SkillItem name="原型制作" icon="🔧" />
   ```

## 🎯 完成检查

- [ ] 成功搭建了 Vite + React 开发环境
- [ ] 理解了 JSX 语法与 HTML 的区别
- [ ] 创建了第一个 React 组件并成功运行
- [ ] 体验了组件的 import/export 机制
- [ ] 了解了"组件化"的基本概念
- [ ] 与 AI 协作完成了 HTML 到 JSX 的转换
- [ ] 建立了"React 组件=Figma 组件"的思维连接

## 🚀 恭喜你！

**你刚刚进入了 React 开发的世界！** 🎉

现在你知道了：

- ⚛️ React 组件就像 Figma 中的可复用组件
- 📝 JSX 让你在 JavaScript 中写类似 HTML 的代码
- 🔄 组件可以独立创建、导入和使用
- 🤖 AI 可以帮助你快速转换 HTML 到 React

**这个 React 页面和 HTML 页面看起来一样，但背后的威力完全不同！**

React 组件具有了"智能"和"可配置性"，这是静态 HTML 无法比拟的。

## 🎯 下一步

现在你有了第一个 React 组件，是时候让它变得更加强大和可配置了！

继续学习：[EP02: 组件 Props 设计 + 样式处理](../EP02-component-props-design/) - 让你的组件变得可配置和可复用

---

**设计师洞察**：React 组件就像你在 Figma 中创建的 Master Component，可以在任何地方重复使用，并且可以通过参数（Props）来配置不同的显示效果。这种思维方式将彻底改变你对 UI 构建的理解。🎨→⚛️✨
