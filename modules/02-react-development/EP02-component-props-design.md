---
layout: default
title: EP02：组件Props设计 + 样式处理
permalink: /modules/02-react-development/EP02-component-props-design/
---

# EP02: 组件Props设计 + 样式处理 ⏱️ 45分钟

**🎧 EP02 配套播客**：
**🎵 可复用组件设计：Props和样式的最佳实践**

- [🎧 Internet Archive 收听](https://archive.org/details/02-ep-02-component-props-design) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/02-ep-02-component-props) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**让组件变得可配置和可复用**：

- 理解Props作为"组件参数"的概念 🎛️
- 设计清晰的组件接口（Props结构）📋
- 处理组件样式和CSS模块化 🎨
- 实现组件的不同变体（如按钮的不同状态）🔄

**这45分钟将让你创建真正可复用的React组件！** 🚀

## 🎛️ Props概念理解：组件的参数系统（10分钟）

### Props = Figma组件的属性面板

**在Figma中**，你会这样配置组件：
1. 选择一个按钮组件
2. 在属性面板中修改：文字、颜色、大小
3. 组件根据设置显示不同效果

**在React中**，Props就是"属性面板"：

```jsx
// 定义组件时接收props参数
function Button(props) {
  return (
    <button className={`btn btn-${props.color}`}>
      {props.text}
    </button>
  )
}

// 使用组件时传入不同的props
<Button text="保存" color="primary" />
<Button text="取消" color="secondary" />
```

### 第一步：改造PersonalIntro组件

将EP01的`PersonalIntro.jsx`改为可配置的：

```jsx
function PersonalIntro(props) {
  return (
    <header>
      <h1>{props.name}</h1>
      <h2>{props.title}</h2>
      <p>{props.description}</p>
    </header>
  )
}

export default PersonalIntro
```

**在App.jsx中使用**：
```jsx
import PersonalIntro from './PersonalIntro'

function App() {
  return (
    <div className="App">
      <PersonalIntro
        name="张小明"
        title="UI/UX 设计师"
        description="你好！我是一名专注于用户体验设计的UI设计师，现在正在学习React开发。"
      />
      {/* 其他内容... */}
    </div>
  )
}
```

**核心理解**：
- `props` = 组件接收的所有参数
- `{props.name}` = 在JSX中显示参数值
- 传入不同的props，组件显示不同内容

## 🎨 创建可复用的Button组件（15分钟）

### 第一步：分析Button的设计需求

**设计师思维分析**：
- 按钮需要不同的**类型**：主要按钮、次要按钮
- 按钮需要不同的**大小**：大、中、小
- 按钮需要不同的**状态**：正常、禁用
- 按钮需要可配置的**文字**

### 第二步：创建Button组件

创建 `src/components/Button.jsx`：

```jsx
function Button(props) {
  // 根据props组合className
  const buttonClass = [
    'btn',
    `btn-${props.type || 'primary'}`,    // 默认为primary
    `btn-${props.size || 'medium'}`,     // 默认为medium
    props.disabled ? 'btn-disabled' : ''
  ].join(' ')

  return (
    <button
      className={buttonClass}
      disabled={props.disabled}
      onClick={props.onClick}
    >
      {props.children}
    </button>
  )
}

export default Button
```

### 第三步：添加Button样式

创建 `src/components/Button.css`：

```css
/* 基础按钮样式 */
.btn {
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

/* 按钮类型 */
.btn-primary {
  background-color: #007bff;
  color: white;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.btn-secondary {
  background-color: #6c757d;
  color: white;
}

.btn-secondary:hover {
  background-color: #545b62;
}

/* 按钮大小 */
.btn-small {
  padding: 6px 12px;
  font-size: 14px;
}

.btn-medium {
  padding: 8px 16px;
  font-size: 16px;
}

.btn-large {
  padding: 12px 24px;
  font-size: 18px;
}

/* 禁用状态 */
.btn-disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

**在Button.jsx中导入样式**：
```jsx
import './Button.css'

function Button(props) {
  // ... 组件代码
}
```

### 第四步：使用Button组件

在`App.jsx`中测试不同的按钮：

{% raw %}
```jsx
import Button from './components/Button'

function App() {
  return (
    <div className="App">
      <PersonalIntro
        name="张小明"
        title="UI/UX 设计师"
        description="你好！我是一名专注于用户体验设计的UI设计师。"
      />

      {/* 测试不同的按钮 */}
      <section style={{padding: '20px', gap: '10px', display: 'flex'}}>
        <Button type="primary" size="large">主要按钮</Button>
        <Button type="secondary" size="medium">次要按钮</Button>
        <Button type="primary" size="small">小按钮</Button>
        <Button disabled>禁用按钮</Button>
      </section>
    </div>
  )
}
```
{% endraw %}

**🎉 成功！** 你刚刚创建了一个完全可配置的Button组件！

## 💳 创建Card组件：内容容器（10分钟）

### 设计Card组件的Props接口

```jsx
// 创建 src/components/Card.jsx
import './Card.css'

function Card(props) {
  return (
    <div className={`card ${props.shadow ? 'card-shadow' : ''}`}>
      {props.title && (
        <div className="card-header">
          <h3>{props.title}</h3>
        </div>
      )}
      <div className="card-body">
        {props.children}
      </div>
      {props.footer && (
        <div className="card-footer">
          {props.footer}
        </div>
      )}
    </div>
  )
}

export default Card
```

### Card样式

创建 `src/components/Card.css`：

```css
.card {
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 20px;
}

.card-shadow {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.card-header {
  padding: 16px 20px;
  border-bottom: 1px solid #e0e0e0;
  background-color: #f8f9fa;
}

.card-header h3 {
  margin: 0;
  color: #333;
}

.card-body {
  padding: 20px;
}

.card-footer {
  padding: 12px 20px;
  border-top: 1px solid #e0e0e0;
  background-color: #f8f9fa;
  text-align: right;
}
```

### 使用Card组件

```jsx
import Card from './components/Card'
import Button from './components/Button'

function App() {
  return (
    <div className="App">
      <PersonalIntro
        name="张小明"
        title="UI/UX 设计师"
        description="你好！我是一名专注于用户体验设计的UI设计师。"
      />

      <Card
        title="我的技能"
        shadow
        footer={<Button type="primary" size="small">查看更多</Button>}
      >
        <ul>
          <li>用户界面设计（UI Design）</li>
          <li>用户体验设计（UX Design）</li>
          <li>原型制作（Prototyping）</li>
          <li>React开发（学习中）</li>
        </ul>
      </Card>

      <Card title="项目经验">
        <p>电商App界面设计 - 为某知名电商平台设计移动端购物应用</p>
        <p>企业官网重设计 - 为科技公司重新设计官方网站</p>
      </Card>
    </div>
  )
}
```

## 🤖 AI协作：组件设计优化（5分钟）

### Props接口设计

在Codex中尝试这些组件设计优化：

1. **Button组件扩展**
   ```
   我的Button组件还需要支持：
   - 图标按钮（icon + text）
   - 加载状态（loading）
   - 圆形按钮（rounded）
   请帮我设计Props接口和实现方案
   ```

2. **Input组件创建**
   ```
   创建一个Input组件，需要支持：
   - 不同类型（text, email, password）
   - placeholder文本
   - 错误状态显示
   - label标签
   ```

3. **组件样式优化**
   ```
   我想让组件支持主题色配置：
   - 主色调可以通过props传入
   - 自动生成hover和active状态颜色
   - 如何实现动态样式？
   ```

### 理解AI的组件设计建议

当你问AI组件设计问题时，关注这些模式：

```
"如何设计一个灵活的组件？"
→ AI会建议使用props + 默认值 + 条件渲染

"组件的样式怎么管理？"
→ AI会建议CSS类组合 + CSS变量 + 样式隔离

"什么时候需要拆分组件？"
→ AI会建议单一职责原则 + 复用性考虑
```

## 🧠 设计师的组件设计思维（3分钟）

### Props设计 = 设计系统规范

**优秀的Props设计原则**：
- ✅ **直观易懂**：`<Button type="primary">` 比 `<Button isPrimary>` 更清晰
- ✅ **一致性**：所有组件都用 `size` 属性（small/medium/large）
- ✅ **合理默认**：最常用的情况不需要传入props
- ✅ **灵活扩展**：支持未来需求的变化

### 组件变体 = Figma的组件变体

**在Figma中**：
- 你创建按钮组件的不同变体
- 每个变体有不同的属性组合
- 使用时选择需要的变体

**在React中**：
- 通过不同的Props组合创建"变体"
- `<Button type="primary" size="large">` = 主要大按钮变体
- `<Button type="secondary" disabled>` = 次要禁用按钮变体

### 快速组件设计实验

在Codex中尝试这些组件设计挑战：

1. **Icon组件设计**
   ```
   设计一个Icon组件，支持：
   - 图标名称（name）
   - 大小（size）
   - 颜色（color）
   - 点击事件（onClick）
   ```

2. **Avatar组件设计**
   ```
   创建头像组件，支持：
   - 图片URL（src）
   - 姓名首字母显示（fallback）
   - 圆形/方形样式（shape）
   - 不同大小（size）
   ```

## 🎯 完成检查

- [ ] 理解了Props作为组件参数的概念
- [ ] 成功创建了可配置的PersonalIntro组件
- [ ] 设计并实现了Button组件的完整Props接口
- [ ] 创建了Card组件并掌握了children prop的使用
- [ ] 学会了组件样式的模块化管理
- [ ] 了解了组件变体的设计思维
- [ ] 与AI协作优化了组件接口设计
- [ ] 建立了"Props=Figma属性面板"的思维连接

## 🚀 恭喜你！

**你刚刚掌握了React组件设计的核心技能！** 🎉

现在你知道了：
- 🎛️ Props让组件变得可配置，就像Figma的属性面板
- 🔧 组件接口设计的重要性和最佳实践
- 🎨 CSS模块化让样式管理更清晰
- 🔄 组件变体通过Props组合实现
- 🤖 AI可以帮助你设计更好的组件接口

**现在你的组件不仅可以重复使用，还可以通过Props灵活配置！**

这就是React组件化开发的真正威力 - 一次创建，到处使用，灵活配置。

## 🎯 下一步

现在你有了可配置的组件，是时候让它们变得"智能"和"互动"了！

继续学习：[EP03: 状态管理 + 用户交互](../EP03-state-management-interaction/) - 让你的组件能够响应用户操作和管理内部状态

---

**设计师洞察**：Props就是组件的"设计规范"，它定义了组件可以如何被配置和使用。良好的Props设计就像优秀的设计系统规范一样，既要灵活够用，又要简单易懂。掌握了Props设计，你就掌握了创建可维护组件库的关键技能。🎨→🎛️✨