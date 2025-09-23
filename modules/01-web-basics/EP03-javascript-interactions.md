---
layout: default
title: EP03：JavaScript交互生活 - 让页面动起来
permalink: /modules/01-web-basics/EP03-javascript-interactions/
---

# EP03: JavaScript交互生活 - 让页面动起来 ⏱️ 40分钟

## 🎯 这一步要完成什么

**JavaScript基础的设计师应用**：
- 为EP02的美观页面添加实用的交互功能 ✨
- 实现暗黑模式切换、平滑滚动、动态效果 🎭
- 理解JavaScript如何让网页"活"起来 ⚡
- 学习事件驱动编程的基础概念 🎯

**这40分钟将让你的静态页面变成动态体验！** 🚀

## ✨ JavaScript = 设计原型中的交互逻辑（5分钟）

### JavaScript的作用

如果把网页比作一个App：
- **HTML** = App的界面结构和内容
- **CSS** = App的视觉样式和美观度
- **JavaScript** = App的交互逻辑和动态行为

**设计师的理解角度**：
- 在Figma/Principle中：设计交互原型、定义动画、处理用户操作
- 在JavaScript中：编写交互代码、实现动画、响应用户事件

### 常见的JavaScript应用场景

- **暗黑模式切换** = 用户点击按钮，整个页面主题改变
- **表单验证** = 用户输入错误，实时显示提示信息
- **平滑滚动** = 点击导航，页面平滑滚动到目标区域
- **动态内容** = 根据用户操作显示或隐藏内容

## 🎭 为个人主页添加交互功能（25分钟）

### 基础交互版本

让我们为EP02的页面添加JavaScript功能。在 `</body>` 标签前添加以下代码：

```html
<!-- 在EP02的HTML基础上，添加交互元素和JavaScript -->
<!DOCTYPE html>
<html lang="zh">
<head>
    <!-- EP02的所有CSS代码保持不变 -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>张小明 - UI设计师个人主页</title>

    <style>
        /* EP02的所有CSS样式保持不变，再添加新的样式 */

        /* 深色模式相关样式 */
        body.dark-mode {
            background-color: #0f172a;
            color: #e2e8f0;
        }

        .dark-mode main section {
            background: #1e293b;
            color: #e2e8f0;
        }

        .dark-mode h1, .dark-mode h2, .dark-mode h3, .dark-mode h4 {
            color: #60a5fa;
        }

        .dark-mode p, .dark-mode li {
            color: #cbd5e1;
        }

        .dark-mode article {
            background: #334155;
            border-left-color: #475569;
        }

        .dark-mode article:hover {
            background: #475569;
        }

        /* 主题切换按钮 */
        .theme-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--primary-color);
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            cursor: pointer;
            font-size: 1.2rem;
            box-shadow: var(--shadow);
            transition: var(--transition);
            z-index: 1000;
        }

        .theme-toggle:hover {
            transform: scale(1.1);
        }

        /* 回到顶部按钮 */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: var(--primary-color);
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            cursor: pointer;
            font-size: 1.2rem;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
            z-index: 1000;
        }

        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            transform: scale(1.1);
        }

        /* 联系表单样式 */
        .contact-form {
            margin-top: 20px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: var(--text-primary);
            font-weight: 500;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            font-size: 14px;
            transition: var(--transition);
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary-color);
        }

        .submit-btn {
            background: var(--primary-color);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            transition: var(--transition);
        }

        .submit-btn:hover {
            background: #1d4ed8;
            transform: translateY(-2px);
        }

        /* 技能进度条 */
        .skill-item {
            margin-bottom: 15px;
        }

        .skill-name {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }

        .skill-bar {
            height: 8px;
            background: #e2e8f0;
            border-radius: 4px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, var(--primary-color), #60a5fa);
            border-radius: 4px;
            width: 0;
            transition: width 1s ease-in-out;
        }
    </style>
</head>
<body>
    <!-- 主题切换按钮 -->
    <button class="theme-toggle" onclick="toggleTheme()" title="切换深色模式">
        🌙
    </button>

    <!-- 回到顶部按钮 -->
    <button class="back-to-top" onclick="scrollToTop()" title="回到顶部">
        ↑
    </button>

    <main>
        <!-- 个人介绍区域 -->
        <section>
            <h1>张小明</h1>
            <h2>UI/UX 设计师</h2>
            <p>你好！我是一名专注于用户体验设计的UI设计师，热爱创造美好的数字体验。</p>
            <p>目前我正在学习前端开发，希望能够更好地将设计想法变为现实。</p>
        </section>

        <!-- 技能区域 - 添加动态进度条 -->
        <section>
            <h3>我的技能</h3>
            <div class="skill-item">
                <div class="skill-name">
                    <span>UI/UX 设计</span>
                    <span>90%</span>
                </div>
                <div class="skill-bar">
                    <div class="skill-progress" data-width="90"></div>
                </div>
            </div>
            <div class="skill-item">
                <div class="skill-name">
                    <span>原型制作</span>
                    <span>85%</span>
                </div>
                <div class="skill-bar">
                    <div class="skill-progress" data-width="85"></div>
                </div>
            </div>
            <div class="skill-item">
                <div class="skill-name">
                    <span>设计系统</span>
                    <span>80%</span>
                </div>
                <div class="skill-bar">
                    <div class="skill-progress" data-width="80"></div>
                </div>
            </div>
            <div class="skill-item">
                <div class="skill-name">
                    <span>前端开发</span>
                    <span>60%</span>
                </div>
                <div class="skill-bar">
                    <div class="skill-progress" data-width="60"></div>
                </div>
            </div>
        </section>

        <!-- EP02的其他section保持不变 -->
        <section>
            <h3>常用设计工具</h3>
            <ul>
                <li>Figma - 界面设计和团队协作</li>
                <li>Sketch - 界面设计</li>
                <li>Adobe XD - 原型设计</li>
                <li>Principle - 交互动效</li>
            </ul>
        </section>

        <!-- 联系我区域 - 添加交互表单 -->
        <section>
            <h3>联系我</h3>
            <p>如果你对我的工作感兴趣，欢迎联系我：</p>
            <ul>
                <li>邮箱：zhangxiaoming@email.com</li>
                <li>微信：designer_zhang</li>
                <li>作品集：<a href="https://dribbble.com/zhangxiaoming">查看我的作品</a></li>
            </ul>

            <!-- 联系表单 -->
            <div class="contact-form">
                <h4>快速联系表单</h4>
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">姓名</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">邮箱</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="message">留言</label>
                        <textarea id="message" name="message" rows="4" required></textarea>
                    </div>
                    <button type="submit" class="submit-btn">发送留言</button>
                </form>
            </div>
        </section>

        <section>
            <h3>项目经验</h3>
            <article>
                <h4>电商App界面设计</h4>
                <p>为某知名电商平台设计移动端购物应用，优化了购买流程，提升了用户转化率。</p>
                <p>使用工具：Figma, Principle</p>
            </article>
            <article>
                <h4>企业官网重设计</h4>
                <p>为科技公司重新设计官方网站，提升了品牌形象和用户体验。</p>
                <p>使用工具：Sketch, Adobe XD</p>
            </article>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 张小明. 保留所有权利.</p>
    </footer>

    <!-- JavaScript 交互代码 -->
    <script>
        // 1. 主题切换功能
        function toggleTheme() {
            const body = document.body;
            const themeButton = document.querySelector('.theme-toggle');

            // 切换深色模式class
            body.classList.toggle('dark-mode');

            // 更新按钮图标
            if (body.classList.contains('dark-mode')) {
                themeButton.textContent = '☀️';
                // 保存用户偏好到本地存储
                localStorage.setItem('theme', 'dark');
            } else {
                themeButton.textContent = '🌙';
                localStorage.setItem('theme', 'light');
            }
        }

        // 2. 页面加载时恢复主题设置
        document.addEventListener('DOMContentLoaded', function() {
            const savedTheme = localStorage.getItem('theme');
            const themeButton = document.querySelector('.theme-toggle');

            if (savedTheme === 'dark') {
                document.body.classList.add('dark-mode');
                themeButton.textContent = '☀️';
            }
        });

        // 3. 回到顶部功能
        function scrollToTop() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }

        // 4. 滚动时显示/隐藏回到顶部按钮
        window.addEventListener('scroll', function() {
            const backToTopButton = document.querySelector('.back-to-top');

            if (window.pageYOffset > 300) {
                backToTopButton.classList.add('visible');
            } else {
                backToTopButton.classList.remove('visible');
            }
        });

        // 5. 技能进度条动画
        function animateSkillBars() {
            const skillBars = document.querySelectorAll('.skill-progress');

            skillBars.forEach(bar => {
                const width = bar.getAttribute('data-width');
                bar.style.width = width + '%';
            });
        }

        // 6. 页面加载完成后触发技能条动画
        window.addEventListener('load', function() {
            setTimeout(animateSkillBars, 500);
        });

        // 7. 表单提交处理
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault(); // 阻止表单默认提交

            // 获取表单数据
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;

            // 简单的表单验证
            if (name.length < 2) {
                alert('请输入有效的姓名');
                return;
            }

            if (!email.includes('@')) {
                alert('请输入有效的邮箱地址');
                return;
            }

            if (message.length < 10) {
                alert('留言内容至少需要10个字符');
                return;
            }

            // 模拟发送成功
            alert(`感谢 ${name} 的留言！我会尽快回复您的邮箱 ${email}`);

            // 重置表单
            this.reset();
        });

        // 8. 为页面添加淡入效果
        document.addEventListener('DOMContentLoaded', function() {
            const sections = document.querySelectorAll('section');
            sections.forEach((section, index) => {
                section.style.opacity = '0';
                section.style.transform = 'translateY(30px)';
                section.style.transition = 'opacity 0.6s ease, transform 0.6s ease';

                setTimeout(() => {
                    section.style.opacity = '1';
                    section.style.transform = 'translateY(0)';
                }, index * 200);
            });
        });
    </script>
</body>
</html>
```

### 体验所有交互功能

1. **保存并刷新页面**
2. **尝试各种交互**：
   - 点击右上角的🌙按钮切换深色模式
   - 滚动页面看回到顶部按钮出现
   - 观察技能条的动画效果
   - 填写并提交联系表单
   - 看页面加载时的淡入动画

🎉 **神奇的交互体验**：同样的内容，加上JavaScript后完全活了过来！

## 🤖 AI协作：增强交互功能（8分钟）

### 个性化交互改进

在Codex中尝试这些JavaScript优化：

#### 1. 添加更多动画效果
```
我想为个人主页添加更丰富的动画效果：
- 鼠标悬停在技能条上时有放大效果
- 项目卡片点击时有翻转动画
- 表单提交成功时有庆祝动画

请帮我实现这些交互增强。
```

#### 2. 优化用户体验
```
我想优化页面的用户体验：
- 添加页面加载进度条
- 实现表单输入的实时验证提示
- 添加键盘导航支持（按ESC关闭弹窗等）

请给出具体的JavaScript实现方案。
```

#### 3. 添加实用功能
```
我想添加一些实用的功能：
- 打印友好的页面样式
- 分享到社交媒体的功能
- 访问计数器
- 简单的联系表单邮件发送

请帮我实现这些功能。
```

### 性能优化建议

#### 4. 代码优化
```
我的JavaScript代码越来越多，想要：
- 将代码组织得更有结构
- 提高代码的性能
- 添加错误处理
- 让代码更容易维护

请给出最佳实践建议。
```

## 🧠 JavaScript基础概念解析（2分钟）

### 事件驱动编程 = 用户操作触发响应

```javascript
// 监听用户点击事件
button.addEventListener('click', function() {
    // 用户点击时执行的代码
    console.log('按钮被点击了！');
});

// 监听页面滚动事件
window.addEventListener('scroll', function() {
    // 用户滚动时执行的代码
    console.log('页面在滚动');
});
```

**设计师理解**：就像Figma中的交互原型
- "当用户点击按钮时" → `addEventListener('click')`
- "页面切换到下一帧" → 执行相应的JavaScript函数

### DOM操作 = 动态修改页面内容

```javascript
// 选择页面元素
const element = document.querySelector('.my-element');

// 修改内容
element.textContent = '新的文字';

// 修改样式
element.style.color = 'blue';

// 添加/移除CSS类
element.classList.add('active');
element.classList.remove('hidden');
```

### JavaScript函数 = 可复用的交互逻辑

```javascript
// 定义一个函数
function showMessage(message) {
    alert(message);
}

// 调用函数
showMessage('你好，设计师！');
```

**设计师对应关系**：
- 函数 = Figma中的组件
- 参数 = 组件的可变属性
- 调用 = 使用组件实例

## 🎯 完成检查

- [ ] 成功为页面添加了JavaScript交互功能
- [ ] 体验了暗黑模式切换的效果
- [ ] 看到了技能进度条的动画
- [ ] 测试了表单验证和提交功能
- [ ] 理解了事件驱动编程的概念
- [ ] 学会了基本的DOM操作
- [ ] 与AI协作优化了交互体验
- [ ] 建立了"JavaScript = 交互逻辑"的认知

## 🚀 恭喜你！

**你刚刚让静态页面拥有了生命！** 🎉

现在你的个人主页具备了：
- ✨ 动态的主题切换功能
- 🎭 流畅的动画和过渡效果
- 📝 实用的表单交互
- 🎯 用户友好的导航体验
- ⚡ 响应式的用户反馈

**你已经掌握了前端开发的三大核心技术：HTML + CSS + JavaScript！**

## 🎯 下一步

现在你的个人主页功能完善、交互丰富，是时候将它扩展为一个完整的个人网站了！

继续学习：[EP04: 完整项目架构](../EP04-complete-project-structure/) - 多页面网站和专业项目结构

---

**设计师的JavaScript启蒙**：

_JavaScript就是网页的"灵魂"。如果说HTML是骨架，CSS是外表，那么JavaScript就是思维和行为。掌握了JavaScript，你就能让设计作品真正"活"起来，响应用户的每一次交互，创造出比静态设计更丰富的用户体验。这就是交互设计的代码实现！_ 🎨→⚡→✨