---
layout: default
title: EP03：状态管理 + 用户交互
permalink: /modules/02-react-development/EP03-state-management-interaction/
---

# EP03: 状态管理 + 用户交互 ⏱️ 40分钟

**🎧 EP03 配套播客**：
**🎵 交互的代码实现：状态管理和事件处理**

- [🎧 Internet Archive 收听](https://archive.org/details/02-ep-03-state-management-interaction) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/02-ep-03-state-management) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**让静态组件变得动态和互动**：

- useState：让组件"记住"信息 🧠
- 事件处理：响应用户点击、输入等操作 👆
- 条件渲染：根据状态显示不同内容 🔄
- 表单控制：处理用户输入和数据提交 📝

**这40分钟将让你的组件真正"活"起来！** ⚡

## 🧠 useState：组件的记忆系统（10分钟）

### State = 组件的内部状态

**在设计中**，你会考虑组件的不同状态：
- 按钮：正常、悬停、点击、禁用
- 输入框：空白、已填写、错误、聚焦
- 模态框：打开、关闭

**在React中**，useState让组件能够"记住"当前状态：

```jsx
import { useState } from 'react'

function Counter() {
  // useState返回[当前值, 更新函数]
  const [count, setCount] = useState(0)

  return (
    <div>
      <p>当前计数：{count}</p>
      <button onClick={() => setCount(count + 1)}>
        点击+1
      </button>
    </div>
  )
}
```

### 第一步：创建主题切换器

创建 `src/components/ThemeToggle.jsx`：

```jsx
import { useState } from 'react'
import './ThemeToggle.css'

function ThemeToggle() {
  // 主题状态：'light' 或 'dark'
  const [theme, setTheme] = useState('light')

  // 切换主题的函数
  const toggleTheme = () => {
    setTheme(theme === 'light' ? 'dark' : 'light')
  }

  return (
    <div className={`theme-toggle ${theme}`}>
      <button
        className="theme-button"
        onClick={toggleTheme}
      >
        {theme === 'light' ? '🌙' : '☀️'}
        {theme === 'light' ? '切换到深色' : '切换到浅色'}
      </button>
      <p>当前主题：{theme}</p>
    </div>
  )
}

export default ThemeToggle
```

### ThemeToggle样式

创建 `src/components/ThemeToggle.css`：

```css
.theme-toggle {
  padding: 20px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.theme-toggle.light {
  background-color: #ffffff;
  color: #333333;
  border: 1px solid #e0e0e0;
}

.theme-toggle.dark {
  background-color: #2d3748;
  color: #ffffff;
  border: 1px solid #4a5568;
}

.theme-button {
  background: none;
  border: 2px solid currentColor;
  color: inherit;
  padding: 8px 16px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.2s ease;
}

.theme-button:hover {
  background-color: currentColor;
  color: var(--bg-color);
}

.light .theme-button:hover {
  color: white;
}

.dark .theme-button:hover {
  color: #2d3748;
}
```

**核心理解**：
- `useState(0)` = 初始状态为0
- `count` = 当前状态值
- `setCount(newValue)` = 更新状态的函数
- 状态改变时，组件会重新渲染

## 👆 事件处理：响应用户操作（10分钟）

### 常见的用户交互事件

**React中的事件处理**：

{% raw %}
```jsx
function InteractiveDemo() {
  const [message, setMessage] = useState('等待用户操作...')

  return (
    <div>
      <p>{message}</p>

      {/* 点击事件 */}
      <button onClick={() => setMessage('按钮被点击了！')}>
        点击我
      </button>

      {/* 鼠标悬停事件 */}
      <div
        onMouseEnter={() => setMessage('鼠标进入了！')}
        onMouseLeave={() => setMessage('鼠标离开了！')}
        style={{padding: '20px', border: '1px solid #ccc', margin: '10px'}}
      >
        悬停区域
      </div>

      {/* 输入事件 */}
      <input
        placeholder="输入文字试试..."
        onChange={(e) => setMessage(`你输入了：${e.target.value}`)}
      />
    </div>
  )
}
```
{% endraw %}

### 创建可交互的导航组件

创建 `src/components/Navigation.jsx`：

```jsx
import { useState } from 'react'
import './Navigation.css'

function Navigation() {
  const [activeTab, setActiveTab] = useState('home')

  const tabs = [
    { id: 'home', label: '首页', icon: '🏠' },
    { id: 'about', label: '关于', icon: '👋' },
    { id: 'portfolio', label: '作品', icon: '💼' },
    { id: 'contact', label: '联系', icon: '📧' }
  ]

  return (
    <nav className="navigation">
      {tabs.map(tab => (
        <button
          key={tab.id}
          className={`nav-tab ${activeTab === tab.id ? 'active' : ''}`}
          onClick={() => setActiveTab(tab.id)}
        >
          <span className="nav-icon">{tab.icon}</span>
          <span className="nav-label">{tab.label}</span>
        </button>
      ))}

      <div className="nav-content">
        <h2>当前页面：{tabs.find(tab => tab.id === activeTab)?.label}</h2>
        <p>你点击了 {tabs.find(tab => tab.id === activeTab)?.label} 标签</p>
      </div>
    </nav>
  )
}

export default Navigation
```

### Navigation样式

创建 `src/components/Navigation.css`：

```css
.navigation {
  width: 100%;
  max-width: 600px;
  margin: 20px auto;
}

.nav-tab {
  background: none;
  border: none;
  padding: 12px 20px;
  margin-right: 8px;
  border-radius: 8px 8px 0 0;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.2s ease;
  border-bottom: 3px solid transparent;
}

.nav-tab:hover {
  background-color: #f0f0f0;
}

.nav-tab.active {
  background-color: #007bff;
  color: white;
  border-bottom-color: #0056b3;
}

.nav-icon {
  font-size: 18px;
}

.nav-label {
  font-weight: 500;
}

.nav-content {
  background-color: #f8f9fa;
  padding: 30px;
  border-radius: 0 8px 8px 8px;
  border: 1px solid #e0e0e0;
}

.nav-content h2 {
  margin: 0 0 10px 0;
  color: #007bff;
}

.nav-content p {
  margin: 0;
  color: #666;
}
```

## 📝 表单处理：用户输入管理（12分钟）

### 受控组件 vs 非受控组件

**受控组件**：React控制表单元素的值
```jsx
function ControlledInput() {
  const [value, setValue] = useState('')

  return (
    <input
      value={value}                           // React控制值
      onChange={(e) => setValue(e.target.value)} // React处理变化
    />
  )
}
```

### 创建联系表单组件

创建 `src/components/ContactForm.jsx`：

```jsx
import { useState } from 'react'
import './ContactForm.css'

function ContactForm() {
  // 表单数据状态
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  })

  // 表单验证状态
  const [errors, setErrors] = useState({})

  // 提交状态
  const [isSubmitting, setIsSubmitting] = useState(false)
  const [isSubmitted, setIsSubmitted] = useState(false)

  // 处理输入变化
  const handleChange = (e) => {
    const { name, value } = e.target
    setFormData(prev => ({
      ...prev,
      [name]: value
    }))

    // 清除该字段的错误
    if (errors[name]) {
      setErrors(prev => ({
        ...prev,
        [name]: ''
      }))
    }
  }

  // 验证表单
  const validateForm = () => {
    const newErrors = {}

    if (!formData.name.trim()) {
      newErrors.name = '请输入姓名'
    }

    if (!formData.email.trim()) {
      newErrors.email = '请输入邮箱'
    } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
      newErrors.email = '邮箱格式不正确'
    }

    if (!formData.message.trim()) {
      newErrors.message = '请输入留言内容'
    }

    return newErrors
  }

  // 处理表单提交
  const handleSubmit = async (e) => {
    e.preventDefault()

    const newErrors = validateForm()
    if (Object.keys(newErrors).length > 0) {
      setErrors(newErrors)
      return
    }

    setIsSubmitting(true)

    // 模拟API提交
    setTimeout(() => {
      console.log('表单数据:', formData)
      setIsSubmitting(false)
      setIsSubmitted(true)

      // 重置表单
      setFormData({ name: '', email: '', message: '' })
    }, 2000)
  }

  if (isSubmitted) {
    return (
      <div className="form-success">
        <h3>✅ 消息发送成功！</h3>
        <p>感谢你的留言，我会尽快回复。</p>
        <button onClick={() => setIsSubmitted(false)}>
          发送另一条消息
        </button>
      </div>
    )
  }

  return (
    <form className="contact-form" onSubmit={handleSubmit}>
      <h3>联系我</h3>

      <div className="form-group">
        <label htmlFor="name">姓名</label>
        <input
          type="text"
          id="name"
          name="name"
          value={formData.name}
          onChange={handleChange}
          className={errors.name ? 'error' : ''}
        />
        {errors.name && <span className="error-message">{errors.name}</span>}
      </div>

      <div className="form-group">
        <label htmlFor="email">邮箱</label>
        <input
          type="email"
          id="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
          className={errors.email ? 'error' : ''}
        />
        {errors.email && <span className="error-message">{errors.email}</span>}
      </div>

      <div className="form-group">
        <label htmlFor="message">留言</label>
        <textarea
          id="message"
          name="message"
          rows="4"
          value={formData.message}
          onChange={handleChange}
          className={errors.message ? 'error' : ''}
        />
        {errors.message && <span className="error-message">{errors.message}</span>}
      </div>

      <button
        type="submit"
        disabled={isSubmitting}
        className="submit-button"
      >
        {isSubmitting ? '发送中...' : '发送消息'}
      </button>
    </form>
  )
}

export default ContactForm
```

### ContactForm样式

创建 `src/components/ContactForm.css`：

```css
.contact-form {
  max-width: 500px;
  margin: 20px auto;
  padding: 30px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.contact-form h3 {
  margin: 0 0 24px 0;
  color: #333;
  text-align: center;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
  color: #555;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 10px 12px;
  border: 2px solid #e0e0e0;
  border-radius: 6px;
  font-size: 16px;
  transition: border-color 0.2s ease;
  box-sizing: border-box;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #007bff;
}

.form-group input.error,
.form-group textarea.error {
  border-color: #dc3545;
}

.error-message {
  display: block;
  color: #dc3545;
  font-size: 14px;
  margin-top: 4px;
}

.submit-button {
  width: 100%;
  padding: 12px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.submit-button:hover:not(:disabled) {
  background-color: #0056b3;
}

.submit-button:disabled {
  background-color: #6c757d;
  cursor: not-allowed;
}

.form-success {
  max-width: 500px;
  margin: 20px auto;
  padding: 30px;
  background: #d4edda;
  border: 1px solid #c3e6cb;
  border-radius: 8px;
  text-align: center;
}

.form-success h3 {
  color: #155724;
  margin: 0 0 16px 0;
}

.form-success p {
  color: #155724;
  margin: 0 0 20px 0;
}

.form-success button {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 6px;
  cursor: pointer;
}
```

## 🤖 AI协作：交互逻辑优化（5分钟）

### 状态管理模式

在Codex中尝试这些交互功能优化：

1. **多步骤表单**
   ```
   创建一个多步骤注册表单：
   - 第一步：基本信息（姓名、邮箱）
   - 第二步：个人资料（头像、简介）
   - 第三步：确认信息
   用useState管理当前步骤和表单数据
   ```

2. **搜索功能**
   ```
   实现一个实时搜索组件：
   - 输入框：用户输入搜索关键词
   - 结果列表：根据关键词过滤显示
   - 高亮匹配：突出显示匹配的文字
   ```

3. **模态框组件**
   ```
   创建一个可复用的Modal组件：
   - 打开/关闭状态管理
   - 背景点击关闭功能
   - ESC键关闭功能
   - 动画过渡效果
   ```

### 理解AI的状态管理建议

当你问AI状态管理问题时，关注这些模式：

```
"什么时候需要使用useState？"
→ AI会建议组件需要"记住"信息时使用

"如何管理复杂的表单状态？"
→ AI会建议对象状态 + 解构赋值 + 统一更新函数

"父子组件如何共享状态？"
→ AI会建议状态提升到共同父组件
```

## 🧠 设计师的交互思维训练（3分钟）

### 状态 = 设计中的组件状态

**在设计中**，你经常考虑：
- 按钮的hover、active、disabled状态
- 输入框的empty、filled、error、focus状态
- 模态框的open、close状态

**在React中**，useState就是管理这些状态：
```jsx
const [isHovered, setIsHovered] = useState(false)
const [isDisabled, setIsDisabled] = useState(false)
const [isModalOpen, setIsModalOpen] = useState(false)
```

### 交互设计 = 事件处理 + 状态更新

**设计交互流程**：
1. 用户操作（点击、输入、悬停）
2. 状态改变（按钮变色、显示消息、打开弹窗）
3. 视觉反馈（动画、提示、页面更新）

**React实现**：
1. 事件处理函数（onClick、onChange、onSubmit）
2. 状态更新（setState调用）
3. 条件渲染（根据状态显示不同内容）

### 快速交互实验

在Codex中尝试这些交互挑战：

1. **图片轮播器**
   ```
   创建图片轮播组件：
   - 当前图片索引状态
   - 下一张/上一张按钮
   - 自动播放功能
   - 指示器点击切换
   ```

2. **评分组件**
   ```
   实现星级评分：
   - 当前评分状态（1-5星）
   - 鼠标悬停预览效果
   - 点击确认评分
   - 已评分状态显示
   ```

## 🎯 完成检查

- [ ] 理解了useState的基本概念和使用方法
- [ ] 成功创建了主题切换器组件
- [ ] 掌握了常见的事件处理方式
- [ ] 实现了可交互的导航组件
- [ ] 学会了受控组件的表单处理
- [ ] 创建了完整的联系表单（包含验证）
- [ ] 了解了条件渲染和状态管理模式
- [ ] 与AI协作优化了交互逻辑
- [ ] 建立了"设计交互→React实现"的思维连接

## 🚀 恭喜你！

**你刚刚让React组件真正"活"了起来！** 🎉

现在你知道了：
- 🧠 useState让组件能够"记住"信息和状态
- 👆 事件处理让组件能够响应用户操作
- 🔄 条件渲染根据状态显示不同内容
- 📝 受控组件让表单处理变得简单可控
- ⚡ 状态 + 事件 = 动态交互的核心

**从静态展示到动态交互，你的组件获得了真正的"生命力"！**

这些交互能力让你能够创建真正实用的用户界面，而不仅仅是静态展示。

## 🎯 下一步

现在你有了能够交互的组件，是时候将它们组织成完整的应用了！

继续学习：[EP04: 项目组织 + 组件整合](../EP04-project-organization/) - 将独立组件组装成完整的React应用

---

**设计师洞察**：useState就是组件的"记忆系统"，它让组件能够在用户交互过程中"记住"和"改变"自己的状态。这和设计中的交互原型完全一致 - 定义状态、响应操作、产生反馈。掌握了状态管理，你就掌握了创建动态用户体验的核心能力。🎨→🧠⚡