---
layout: default
title: EP01：HTML结构基础 - 我的第一个个人主页
permalink: /modules/01-web-basics/EP01-html-basics/
---

# EP01: HTML 结构基础 - 我的第一个个人主页 ⏱️ 30 分钟

**🎧 EP01 配套播客**：
**🎵 HTML 基础入门：设计师的 Web 结构启蒙**

- [🎧 Internet Archive 收听](https://archive.org/details/01-ep-01-html-basics) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/5v7aH5TWMg5fSoFbwrItdo?si=67GxkfGKQw-UrFHnM5gYJw&nd=1&dlsi=88714f8e1fd74c4d) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**HTML 基础的设计师入门**：

- 复制简单的 HTML 个人主页，立即看到效果 ✨
- 修改个人信息：姓名、职位、联系方式 📝
- 理解 HTML 标签的作用和文档结构 🏗️
- 掌握 HTML 语义化和最佳实践 📚

**这 30 分钟将让你理解网页的"骨架"是如何构建的！** 🚀

## ✨ 第一个 HTML 网页：看见网页的骨架（5 分钟）

### 第一步：创建项目文件夹

1. **在桌面创建新文件夹**

   - 文件夹名：`my-personal-website`

2. **创建 HTML 文件**
   - 在文件夹中新建文本文件
   - 重命名为：`index.html`
   - ⚠️ 确保扩展名是 `.html` 而不是 `.txt`

### 第二步：复制基础 HTML 结构

将下面的**纯 HTML 代码**完整复制到 `index.html` 文件中：

```html
<!DOCTYPE html>
<html lang="zh">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>张小明 - UI设计师个人主页</title>
  </head>
  <body>
    <!-- 页面主要内容 -->
    <main>
      <!-- 个人介绍区域 -->
      <section>
        <h1>张小明</h1>
        <h2>UI/UX 设计师</h2>
        <p>
          你好！我是一名专注于用户体验设计的UI设计师，热爱创造美好的数字体验。
        </p>
        <p>目前我正在学习前端开发，希望能够更好地将设计想法变为现实。</p>
      </section>

      <!-- 技能区域 -->
      <section>
        <h3>我的技能</h3>
        <ul>
          <li>用户界面设计（UI Design）</li>
          <li>用户体验设计（UX Design）</li>
          <li>原型制作（Prototyping）</li>
          <li>设计系统（Design Systems）</li>
        </ul>
      </section>

      <!-- 使用工具区域 -->
      <section>
        <h3>常用设计工具</h3>
        <ul>
          <li>Figma - 界面设计和团队协作</li>
          <li>Sketch - 界面设计</li>
          <li>Adobe XD - 原型设计</li>
          <li>Principle - 交互动效</li>
        </ul>
      </section>

      <!-- 联系方式区域 -->
      <section>
        <h3>联系我</h3>
        <p>如果你对我的工作感兴趣，欢迎联系我：</p>
        <ul>
          <li>邮箱：zhangxiaoming@email.com</li>
          <li>微信：designer_zhang</li>
          <li>
            作品集：<a href="https://dribbble.com/zhangxiaoming"
              >查看我的作品</a
            >
          </li>
        </ul>
      </section>

      <!-- 项目经验区域 -->
      <section>
        <h3>项目经验</h3>
        <article>
          <h4>电商App界面设计</h4>
          <p>
            为某知名电商平台设计移动端购物应用，优化了购买流程，提升了用户转化率。
          </p>
          <p>使用工具：Figma, Principle</p>
        </article>
        <article>
          <h4>企业官网重设计</h4>
          <p>为科技公司重新设计官方网站，提升了品牌形象和用户体验。</p>
          <p>使用工具：Sketch, Adobe XD</p>
        </article>
      </section>
    </main>

    <!-- 页脚信息 -->
    <footer>
      <p>&copy; 2024 张小明. 保留所有权利.</p>
    </footer>
  </body>
</html>
```

### 第三步：见证 HTML 的力量 ✨

1. **保存文件** - `Ctrl/Cmd + S`
2. **双击打开** - 双击 `index.html` 文件
3. **观察结果** - 浏览器会显示一个朴素但结构清晰的个人主页！

🎯 **重要观察**：现在的页面看起来很朴素，这就是纯 HTML 的样子。在 EP02 中，我们将用 CSS 让它变得美观！

## 📝 个性化你的个人主页（10 分钟）

### 基础修改练习

现在让我们把这个模板改成你自己的信息。**在 VS Code 的 Codex 面板中输入**：

```
我想把这个HTML个人主页改成我自己的信息：

个人信息：
- 姓名：[你的姓名]
- 职位：[你的职位]
- 自我介绍：[简短介绍]

技能列表：
- [技能1]
- [技能2]
- [技能3]

联系方式：
- 邮箱：[你的邮箱]
- 其他联系方式：[微信/LinkedIn等]

请帮我修改HTML代码中的相应内容。
```

### AI 协作体验

尝试这些修改请求：

#### 1. 添加更多内容

```
我想在个人主页中添加：
- 教育背景部分
- 工作经历部分
- 个人兴趣爱好部分

请帮我添加相应的HTML结构。
```

#### 2. 调整内容结构

```
我想调整页面的结构顺序：
- 把联系方式移到页面顶部
- 把项目经验放在技能后面
- 添加一个"关于我"的详细介绍区域

请帮我重新组织HTML结构。
```

## 🏗️ HTML 基础知识解析（10 分钟）

### HTML 标签 = 设计中的容器和元素

作为设计师，你在 Figma 中会使用各种元素：

**Figma 中的元素** → **HTML 中的标签**

- 文本框 → `<p>`, `<h1>`, `<h2>`, `<span>`
- 组 (Group) → `<div>`, `<section>`, `<article>`
- 列表 → `<ul>`, `<ol>`, `<li>`
- 按钮 → `<button>`, `<a>`
- 图片 → `<img>`

### HTML 文档结构 = 设计文件的图层组织

```html
<!DOCTYPE html>
<!-- 文档类型声明 -->
<html lang="zh">
  <!-- 根元素，整个页面的容器 -->
  <head>
    <!-- 头部：页面信息，用户看不到 -->
    <title>页面标题</title>
    <!-- 浏览器标签页显示的标题 -->
  </head>
  <body>
    <!-- 主体：页面内容，用户看得到 -->
    <!-- 这里放置所有可见内容 -->
  </body>
</html>
```

### 语义化 HTML = 有意义的设计结构

**什么是语义化？**

就像在 Figma 中给图层起有意义的名字一样：

❌ **不好的命名**：Rectangle 1, Group 2, Text 3
✅ **好的命名**：Header, Navigation, Content

**HTML 语义化标签**：

```html
<header>
  <!-- 页面或区域的头部 -->
  <nav>
    <!-- 导航菜单 -->
    <main>
      <!-- 主要内容 -->
      <section>
        <!-- 内容区块 -->
        <article>
          <!-- 独立的文章或内容 -->
          <aside>
            <!-- 侧边栏或相关信息 -->
            <footer><!-- 页面或区域的底部 --></footer>
          </aside>
        </article>
      </section>
    </main>
  </nav>
</header>
```

### 理解 AI 的 HTML 建议

当你问 AI HTML 问题时，关注这些关键概念：

```
"我想添加一个项目展示区域"
→ AI会建议用<section>包含多个<article>

"我想添加一个导航菜单"
→ AI会建议用<nav>包含<ul>和<li>

"我想突出显示重要信息"
→ AI会建议用<strong>或<em>标签
```

## 🧠 设计师的 HTML 思维训练（3 分钟）

### HTML = 内容结构，不是视觉样式

**设计师常见误区**：

- ❌ "这个标题太小了" - HTML 只管内容，不管大小
- ❌ "这个颜色不好看" - HTML 不负责颜色
- ❌ "布局不对齐" - HTML 不负责布局

**正确的 HTML 思维**：

- ✅ "这是一个主标题" - 用`<h1>`
- ✅ "这是一个内容区块" - 用`<section>`
- ✅ "这是一个链接" - 用`<a>`

### 快速 HTML 实验

在 Codex 中尝试这些快速实验：

1. **添加图片**

   ```
   我想在个人介绍区域添加一张头像图片，HTML应该怎么写？
   ```

2. **创建表格**

   ```
   我想用表格展示我的工作经历，包括公司、职位、时间，HTML结构应该怎么组织？
   ```

3. **添加表单**
   ```
   我想添加一个联系表单，包括姓名、邮箱、留言字段，HTML代码应该怎么写？
   ```

## 🎯 完成检查

- [ ] 成功创建了 HTML 文件并在浏览器中打开
- [ ] 看到了纯 HTML 页面的朴素外观
- [ ] 与 AI 协作修改了个人信息内容
- [ ] 理解了 HTML 标签的基本作用
- [ ] 掌握了 HTML 文档的基本结构
- [ ] 了解了语义化 HTML 的重要性
- [ ] 建立了"HTML 管内容，CSS 管样式"的基础认知

## 🚀 恭喜你！

**你刚刚理解了网页的基本构成！** 🎉

现在你知道了：

- ✨ HTML 是网页的"骨架"，负责内容和结构
- 🏗️ HTML 标签就像 Figma 中的图层和容器
- 📝 语义化的 HTML 让内容更有意义
- 🤖 AI 可以帮助你快速生成和修改 HTML 结构

**这个朴素的页面看起来不够美观？**

这是正常的！HTML 只负责内容结构，视觉美化是 CSS 的工作。

## 🎯 下一步

现在你的个人主页有了清晰的内容结构，是时候让它变得美观了！

继续学习：[EP02: CSS 样式魔法](../EP02-css-styling-magic/) - 让你的 HTML 页面从"程序员审美"变成"设计师作品"

---

**设计师洞察**：HTML 就像你在 Figma 中搭建的图层结构，它定义了内容的组织方式，但不关心外观。这种"结构与样式分离"的思想，其实在设计系统中你也在使用——先定义组件的功能，再定义视觉样式。🎨→🏗️✨
