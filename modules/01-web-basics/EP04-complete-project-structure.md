---
layout: default
title: EP04：完整项目架构 - 多页面个人网站
permalink: /modules/01-web-basics/EP04-complete-project-structure/
---

# EP04: 完整项目架构 - 多页面个人网站 ⏱️ 35 分钟

**🎧 EP04 配套播客**：
**🎵 项目架构设计：从单页面到完整网站**

- [🎧 Internet Archive 收听](https://archive.org/details/01-ep-04-complete-project-structure)
- [🎵 Spotify 收听](https://open.spotify.com/episode/2xlUTCeSBRfw5JUAcqo6VD?si=1lvKBvyUQm2j-D5GaemMIw)

---

## 🎯 这一步要完成什么

**从单页面到完整网站项目**：

- 将 EP03 的单页面扩展为多页面网站结构 🏗️
- 创建专业的导航系统和页面跳转 🧭
- 学习项目文件组织和管理 📁
- 完成 V1.0 个人网站项目 🚀

**这 35 分钟将让你拥有第一个完整的个人网站！** ✨

## 🏗️ 项目结构规划：像设计师一样组织代码（8 分钟）

### 网站结构 = 信息架构设计

作为设计师，你肯定做过网站的信息架构设计：

**设计阶段的信息架构**：

```
个人网站
├── 首页（Home）
├── 关于我（About）
├── 作品集（Portfolio）
├── 服务（Services）
└── 联系我（Contact）
```

**代码项目的文件架构**：

```
my-personal-website/
├── index.html          # 首页
├── about.html           # 关于我
├── portfolio.html       # 作品集
├── services.html        # 服务
├── contact.html         # 联系我
├── css/
│   ├── main.css        # 主样式文件
│   └── components.css  # 组件样式
├── js/
│   ├── main.js         # 主脚本文件
│   └── components.js   # 组件脚本
├── images/             # 图片资源
└── assets/             # 其他资源
```

### 第一步：创建项目文件结构

1. **重新组织项目文件夹**

   - 将原来的`my-personal-website`文件夹重新整理
   - 创建`css`、`js`、`images`子文件夹

2. **分离 CSS 和 JavaScript**
   - 将 CSS 代码提取到独立的`.css`文件
   - 将 JavaScript 代码提取到独立的`.js`文件

### 第二步：创建共享的样式和脚本文件

**创建 `css/main.css` 文件**：

```css
/* 现代设计系统基础 */
:root {
  --primary-color: #2563eb;
  --secondary-color: #64748b;
  --background-color: #f8fafc;
  --text-primary: #1e293b;
  --text-secondary: #64748b;
  --white: #ffffff;
  --border-radius: 12px;
  --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --transition: all 0.3s ease;
  --max-width: 1200px;
}

/* 重置浏览器默认样式 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* 页面整体样式 */
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto",
    "Helvetica", "Arial", sans-serif;
  line-height: 1.6;
  color: var(--text-primary);
  background-color: var(--background-color);
}

/* 导航栏样式 */
.navbar {
  background: var(--white);
  padding: 1rem 0;
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: var(--shadow);
}

.nav-container {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-color);
  text-decoration: none;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
}

.nav-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 500;
  transition: var(--transition);
}

.nav-link:hover,
.nav-link.active {
  color: var(--primary-color);
}

/* 主要内容容器 */
.container {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 2rem;
}

.main-content {
  max-width: 800px;
  margin: 0 auto;
  padding: 40px 0;
}

/* 页面区块样式 */
.section {
  background: var(--white);
  margin-bottom: 30px;
  padding: 30px;
  border-radius: var(--border-radius);
  box-shadow: var(--shadow);
}

/* 标题层次 */
h1 {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

h2 {
  font-size: 1.8rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

h3 {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 1rem;
  border-left: 4px solid var(--primary-color);
  padding-left: 15px;
}

/* 页面标题 */
.page-title {
  text-align: center;
  margin-bottom: 3rem;
}

.page-title h1 {
  margin-bottom: 1rem;
}

.page-subtitle {
  color: var(--text-secondary);
  font-size: 1.1rem;
}

/* 响应式导航 */
.nav-toggle {
  display: none;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
}

@media (max-width: 768px) {
  .nav-menu {
    position: fixed;
    top: 70px;
    left: -100%;
    width: 100%;
    height: calc(100vh - 70px);
    background: var(--white);
    flex-direction: column;
    justify-content: start;
    align-items: center;
    transition: left 0.3s ease;
    padding: 2rem 0;
  }

  .nav-menu.active {
    left: 0;
  }

  .nav-toggle {
    display: block;
  }

  .container {
    padding: 1rem;
  }
}

/* 页脚样式 */
.footer {
  background: var(--text-primary);
  color: var(--white);
  text-align: center;
  padding: 2rem 0;
  margin-top: 4rem;
}

/* 深色模式支持 */
body.dark-mode {
  background-color: #0f172a;
  color: #e2e8f0;
}

.dark-mode .navbar,
.dark-mode .section {
  background: #1e293b;
  color: #e2e8f0;
}

.dark-mode .nav-link {
  color: #cbd5e1;
}
```

### 第三步：创建导航组件

**创建 `js/navigation.js` 文件**：

```javascript
// 导航组件和页面管理
document.addEventListener("DOMContentLoaded", function () {
  // 创建导航栏
  createNavigation();

  // 设置当前页面的导航状态
  setActiveNavItem();

  // 初始化移动端导航
  initMobileNavigation();
});

function createNavigation() {
  // 导航栏HTML结构
  const navHTML = `
        <nav class="navbar">
            <div class="nav-container">
                <a href="index.html" class="nav-logo">张小明</a>
                <ul class="nav-menu">
                    <li><a href="index.html" class="nav-link" data-page="home">首页</a></li>
                    <li><a href="about.html" class="nav-link" data-page="about">关于我</a></li>
                    <li><a href="portfolio.html" class="nav-link" data-page="portfolio">作品集</a></li>
                    <li><a href="services.html" class="nav-link" data-page="services">服务</a></li>
                    <li><a href="contact.html" class="nav-link" data-page="contact">联系我</a></li>
                </ul>
                <button class="nav-toggle">☰</button>
            </div>
        </nav>
    `;

  // 将导航栏插入到页面顶部
  document.body.insertAdjacentHTML("afterbegin", navHTML);
}

function setActiveNavItem() {
  const currentPage = window.location.pathname.split("/").pop() || "index.html";
  const navLinks = document.querySelectorAll(".nav-link");

  navLinks.forEach((link) => {
    const linkPage = link.getAttribute("href");
    if (
      linkPage === currentPage ||
      (currentPage === "index.html" && link.dataset.page === "home")
    ) {
      link.classList.add("active");
    }
  });
}

function initMobileNavigation() {
  const navToggle = document.querySelector(".nav-toggle");
  const navMenu = document.querySelector(".nav-menu");

  navToggle.addEventListener("click", function () {
    navMenu.classList.toggle("active");
  });

  // 点击菜单项时关闭移动端菜单
  const navLinks = document.querySelectorAll(".nav-link");
  navLinks.forEach((link) => {
    link.addEventListener("click", function () {
      navMenu.classList.remove("active");
    });
  });
}
```

## 📝 创建各个页面（20 分钟）

### 页面模板结构

每个页面都使用统一的基础模板：

**创建 `index.html`（首页）**：

```html
<!DOCTYPE html>
<html lang="zh">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>张小明 - UI/UX设计师</title>
    <link rel="stylesheet" href="css/main.css" />
    <link rel="stylesheet" href="css/components.css" />
  </head>
  <body>
    <!-- 导航栏通过JavaScript动态插入 -->

    <div class="container">
      <div class="main-content">
        <!-- 个人介绍区域 -->
        <section class="section">
          <div class="page-title">
            <h1>张小明</h1>
            <p class="page-subtitle">UI/UX 设计师 & 前端开发学习者</p>
          </div>
          <p>
            你好！我是一名专注于用户体验设计的UI设计师，热爱创造美好的数字体验。
          </p>
          <p>目前我正在学习前端开发，希望能够更好地将设计想法变为现实。</p>
        </section>

        <!-- 核心技能快览 -->
        <section class="section">
          <h3>核心技能</h3>
          <div class="skills-grid">
            <div class="skill-card">
              <h4>UI/UX 设计</h4>
              <p>用户界面和体验设计，创造直观易用的产品</p>
            </div>
            <div class="skill-card">
              <h4>原型制作</h4>
              <p>高保真交互原型，快速验证设计想法</p>
            </div>
            <div class="skill-card">
              <h4>设计系统</h4>
              <p>建立可扩展的设计规范和组件库</p>
            </div>
          </div>
        </section>

        <!-- 最新项目展示 -->
        <section class="section">
          <h3>最新项目</h3>
          <div class="project-preview">
            <h4>电商App界面重设计</h4>
            <p>
              为某知名电商平台重新设计移动端用户界面，优化购物流程，提升用户转化率。
            </p>
            <a href="portfolio.html" class="cta-link">查看更多项目 →</a>
          </div>
        </section>
      </div>
    </div>

    <!-- 页脚 -->
    <footer class="footer">
      <p>&copy; 2024 张小明. 保留所有权利.</p>
    </footer>

    <script src="js/navigation.js"></script>
    <script src="js/main.js"></script>
  </body>
</html>
```

**创建 `about.html`（关于我页面）**：

```html
<!DOCTYPE html>
<html lang="zh">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>关于我 - 张小明</title>
    <link rel="stylesheet" href="css/main.css" />
    <link rel="stylesheet" href="css/components.css" />
  </head>
  <body>
    <div class="container">
      <div class="main-content">
        <div class="page-title">
          <h1>关于我</h1>
          <p class="page-subtitle">了解我的设计理念和工作方式</p>
        </div>

        <section class="section">
          <h3>我的故事</h3>
          <p>
            作为一名UI/UX设计师，我始终相信好的设计应该是无形的——它应该如此自然，以至于用户甚至不会注意到它的存在。
          </p>
          <p>
            我的设计哲学是以用户为中心，通过深入的用户研究和数据分析，创造出既美观又实用的产品体验。
          </p>
        </section>

        <section class="section">
          <h3>专业技能</h3>
          <div class="skills-list">
            <div class="skill-category">
              <h4>设计技能</h4>
              <ul>
                <li>用户研究与可用性测试</li>
                <li>信息架构与用户流程设计</li>
                <li>界面设计与视觉设计</li>
                <li>交互原型与动效设计</li>
              </ul>
            </div>
            <div class="skill-category">
              <h4>工具软件</h4>
              <ul>
                <li>Figma - 界面设计协作平台</li>
                <li>Sketch - Mac平台设计工具</li>
                <li>Adobe Creative Suite</li>
                <li>Principle - 交互动效制作</li>
              </ul>
            </div>
          </div>
        </section>

        <section class="section">
          <h3>教育背景</h3>
          <div class="education-item">
            <h4>设计学学士</h4>
            <p>某知名设计学院 | 2018-2022</p>
            <p>主修视觉传达设计，辅修计算机科学</p>
          </div>
        </section>

        <section class="section">
          <h3>工作经历</h3>
          <div class="experience-item">
            <h4>高级UI设计师</h4>
            <p>某互联网公司 | 2022至今</p>
            <p>
              负责移动端产品的界面设计和用户体验优化，参与多个千万级用户产品的设计工作。
            </p>
          </div>
        </section>
      </div>
    </div>

    <footer class="footer">
      <p>&copy; 2024 张小明. 保留所有权利.</p>
    </footer>

    <script src="js/navigation.js"></script>
    <script src="js/main.js"></script>
  </body>
</html>
```

**创建其他页面**（portfolio.html, services.html, contact.html）：

- 使用相同的基础结构
- 根据页面内容调整具体的 section 内容
- 保持导航和页脚的一致性

### 组件样式文件

**创建 `css/components.css` 文件**：

```css
/* 页面组件样式 */

/* 技能网格 */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.skill-card {
  padding: 1.5rem;
  border: 2px solid #e2e8f0;
  border-radius: var(--border-radius);
  transition: var(--transition);
}

.skill-card:hover {
  border-color: var(--primary-color);
  transform: translateY(-5px);
}

.skill-card h4 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

/* 项目预览 */
.project-preview {
  padding: 2rem;
  background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
  border-radius: var(--border-radius);
  margin-top: 1rem;
}

.project-preview h4 {
  color: var(--primary-color);
  margin-bottom: 1rem;
}

.cta-link {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: 1rem;
  transition: var(--transition);
}

.cta-link:hover {
  color: #1d4ed8;
}

/* 技能列表 */
.skills-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.skill-category h4 {
  color: var(--primary-color);
  margin-bottom: 1rem;
}

.skill-category ul {
  list-style: none;
}

.skill-category li {
  padding: 0.5rem 0;
  padding-left: 1.5rem;
  position: relative;
  color: var(--text-secondary);
}

.skill-category li::before {
  content: "▸";
  position: absolute;
  left: 0;
  color: var(--primary-color);
  font-weight: bold;
}

/* 教育和经历项目 */
.education-item,
.experience-item {
  padding: 1.5rem;
  border-left: 4px solid var(--primary-color);
  background: #f8fafc;
  margin: 1rem 0;
  border-radius: 0 var(--border-radius) var(--border-radius) 0;
}

.education-item h4,
.experience-item h4 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

.education-item p:first-of-type,
.experience-item p:first-of-type {
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}
```

## 🤖 AI 协作：完善网站功能（5 分钟）

### 网站优化建议

在 Codex 中尝试这些网站改进：

#### 1. 添加更多页面内容

```
我想完善个人网站的内容：
- 在作品集页面添加项目筛选功能
- 在服务页面添加服务价格表
- 在联系页面添加地图和社交媒体链接
- 创建一个博客页面

请帮我设计这些页面的结构和功能。
```

#### 2. 性能和 SEO 优化

```
我想优化网站的性能和搜索引擎可见性：
- 添加网站图标和meta标签
- 优化图片加载和压缩
- 添加网站地图
- 实现页面间的预加载

请给出具体的优化方案。
```

#### 3. 现代化功能增强

```
我想为网站添加一些现代化功能：
- 添加页面加载进度条
- 实现平滑的页面切换动画
- 添加返回顶部的浮动按钮
- 创建面包屑导航

请帮我实现这些用户体验增强。
```

## 🎯 项目总结和优化（2 分钟）

### 你的 V1.0 个人网站包含了：

✅ **完整的网站架构**

- 5 个主要页面，结构清晰
- 统一的导航系统
- 响应式设计支持

✅ **现代化的技术实现**

- 语义化的 HTML 结构
- 模块化的 CSS 样式系统
- 交互式的 JavaScript 功能

✅ **专业的项目组织**

- 清晰的文件夹结构
- 分离的样式和脚本文件
- 可维护的代码架构

✅ **优秀的用户体验**

- 直观的导航体验
- 一致的视觉设计
- 移动端友好的布局

### 部署到线上

你可以将网站部署到以下平台：

- **GitHub Pages** - 免费的静态网站托管
- **Netlify** - 现代化的部署平台
- **Vercel** - 专注于前端的部署服务

## 🎯 完成检查

- [ ] 成功创建了多页面网站结构
- [ ] 实现了统一的导航系统
- [ ] 组织了清晰的项目文件架构
- [ ] 完成了所有主要页面的内容
- [ ] 测试了页面间的跳转功能
- [ ] 验证了移动端的响应式效果
- [ ] **完成了 V1.0 个人网站项目！** 🎉

## 🚀 恭喜你！Module 01 完美收官！

**你刚刚完成了一个重要的里程碑！** 🎉

从 30 分钟前的零基础，到现在拥有一个完整的个人网站：

- ✨ **HTML 基础** - 理解了网页结构和语义化
- 🎨 **CSS 魔法** - 掌握了样式设计和响应式布局
- ⚡ **JavaScript 交互** - 学会了动态功能和用户交互
- 🏗️ **项目架构** - 建立了完整的网站项目结构

**你不仅学会了技术，更重要的是建立了从设计到代码的思维连接！**

## 🎯 下一步的学习路径

现在你有三个选择：

1. **巩固成果** - 继续完善你的个人网站，添加更多内容和功能
2. **继续深入** - 学习 [Module 02: React 组件化开发](/modules/02-react-development/)
3. **分享作品** - 将网站部署上线，分享给朋友和同事

## 📝 Module 01 学习反思

花几分钟思考一下这个学习过程：

- **最大的收获是什么？** 是否改变了对"编程"的看法？
- **最有成就感的时刻？** 哪个功能实现让你最兴奋？
- **对 AI 协作的感受？** AI 是否成为了你的好伙伴？
- **未来的规划？** 准备如何运用这些新技能？

---

**设计师的编程之路启航**：

_恭喜你完成了从设计师到"会编程的设计师"的华丽转身！你创建的不仅仅是一个网站，更是证明了创意工作者可以直接将想法变为现实。这种能力将彻底改变你的工作方式和创作可能性。_

_这只是开始，更精彩的技术世界还在等着你去探索！_ 🎨💻🚀✨
