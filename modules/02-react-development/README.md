# 模块二：React 组件化开发 ⭐⭐⭐

**作品集版本**：V2.0 组件化重构
**技术栈**：React + Storybook
**产出目标**：组件化作品集网站 + 个人设计系统组件库

## 📖 核心目标

掌握 React 组件化思维，重构作品集为 V2.0：
- 掌握 React 组件化开发思维和最佳实践
- 建立个人设计系统组件库
- 学会使用 Storybook 进行组件文档化
- 完成作品集网站的组件化重构升级

## 🎧 配套播客

- [EP01：从静态到组件化](/podcasts/ep05-static-to-components.md) - 理解组件化思维的转变
- [EP02：设计系统的组件化实现](/podcasts/ep06-design-system-components.md) - 如何将设计规范转化为React组件
- [EP03：状态管理入门](/podcasts/ep07-state-management.md) - useState和useEffect的实际应用
- [EP04：组件库文档化](/podcasts/ep08-component-documentation.md) - Storybook的使用和维护

## 📚 EP 学习路径

### EP01: Node.js 环境 + React 基础（建立React开发环境）

**学习目标**：
- 配置完整的 Node.js 和 React 开发环境
- 掌握 JSX 语法和 React 基础概念
- 理解函数组件和 Hooks 的使用

**学习内容**：
- Node.js 和 npm/yarn 安装配置
- Create React App 或 Vite + React 环境搭建
- JSX 语法理解和最佳实践
- 函数组件的创建和使用
- React Hooks 基础（useState, useEffect）
- 组件设计原则和命名规范

**实践项目**：创建第一个 React 组件并理解组件化概念

### EP02: 设计系统组件化（构建可复用组件库）

**学习目标**：
- 将设计系统转化为 React 组件
- 掌握组件 Props 设计和 TypeScript 基础
- 学会使用 Storybook 进行组件文档化

**学习内容**：
- Button、Card、Input、Form 等基础组件开发
- 组件 Props 接口设计
- TypeScript 在 React 中的应用基础
- Storybook 安装配置和使用
- 组件变体和状态管理
- 样式封装和主题系统

**实践项目**：构建个人设计系统的核心组件库

### EP03: 状态管理 + 用户交互（实现动态交互）

**学习目标**：
- 深入理解 React 状态管理
- 实现复杂的用户交互逻辑
- 掌握表单处理和数据验证

**学习内容**：
- useState 深入使用和状态设计原则
- useEffect 生命周期和副作用处理
- 事件处理和用户交互模式
- 表单组件和数据验证
- 条件渲染和列表渲染
- 组件间通信（props 传递）

**实践项目**：为作品集网站添加动态交互功能

### EP04: 项目重构 + 优化（组件化重构和性能优化）

**学习目标**：
- 将现有静态网站重构为 React 组件
- 掌握性能优化和代码分割技巧
- 建立完整的组件库维护体系

**学习内容**：
- 现有 V1.0 网站的 React 组件化重构
- 组件拆分和结构优化
- React.memo 和 useMemo 性能优化
- 代码分割和懒加载
- 组件库的维护和版本管理
- 测试基础和组件测试

**实践项目**：完成作品集网站 V2.0 组件化重构

## 🛠 核心项目：个人作品集 V2.0

### 项目概览
将 V1.0 的静态作品集网站重构为基于 React 的组件化架构，同时建立个人设计系统组件库。

### 技术架构
```
src/
├── components/           # 可复用组件
│   ├── ui/              # 基础 UI 组件
│   │   ├── Button/
│   │   ├── Card/
│   │   ├── Input/
│   │   └── ...
│   ├── layout/          # 布局组件
│   │   ├── Header/
│   │   ├── Footer/
│   │   └── Navigation/
│   └── sections/        # 页面区块组件
│       ├── Hero/
│       ├── Portfolio/
│       └── Contact/
├── pages/               # 页面组件
├── styles/              # 样式系统
├── utils/               # 工具函数
└── storybook/          # 组件文档
```

### 开发流程
1. **组件设计**：基于 V1.0 网站分析组件结构
2. **基础组件开发**：开发可复用的 UI 组件
3. **页面组件组装**：将基础组件组合成页面
4. **交互逻辑实现**：添加动态交互功能
5. **性能优化**：代码分割和性能调优
6. **文档完善**：Storybook 组件文档

## 🤖 AI 协作学习

### React 开发中的 AI 协作
- **组件设计咨询**："我需要设计一个卡片组件，应该包含哪些 props？"
- **代码生成辅助**：描述组件需求，让 AI 生成初始代码结构
- **调试问题解决**："为什么我的 useState 没有更新？"
- **最佳实践学习**：询问 React 开发的最佳实践和设计模式

### 设计系统开发协作
- **组件变体设计**：与 AI 讨论组件的不同状态和变体
- **接口设计优化**：优化组件 Props 接口的设计
- **样式架构规划**：规划组件样式的组织和复用策略

**AI 协作指南：**
- [React 开发 AI 协作指南](/tools/react-ai-collaboration.md)
- [组件设计提示词模板](/tools/component-design-prompts.md)

## ✅ 模块完成标准

### 技能掌握检验

- [ ] **React 基础能力**：熟练使用函数组件和 Hooks
- [ ] **组件设计能力**：能设计可复用、接口清晰的组件
- [ ] **状态管理能力**：掌握 useState 和 useEffect 的使用
- [ ] **TypeScript 基础**：能为组件编写基础的类型定义
- [ ] **Storybook 使用**：能创建和维护组件文档

### 项目产出检验

- [ ] **V2.0 作品集网站**：React 重构的组件化作品集
- [ ] **个人组件库**：包含 8-10 个基础 UI 组件
- [ ] **Storybook 文档**：完整的组件使用文档和示例
- [ ] **交互功能**：实现动态交互和用户体验优化
- [ ] **代码质量**：组件结构清晰，接口设计合理

### 准备下一模块

- [ ] **Next.js 概念预习**：了解全栈开发和 SSR 概念
- [ ] **TypeScript 深化**：加强 TypeScript 类型系统理解
- [ ] **设计规划**：规划 V3.0 全栈网站的功能需求

## 📚 学习资源

### 官方文档
- [React 官方文档](https://react.dev/) - 新版 React 文档
- [React TypeScript 指南](https://react-typescript-cheatsheet.netlify.app/)
- [Storybook 文档](https://storybook.js.org/docs/react/get-started/introduction)

### 设计系统参考
- [Ant Design](https://ant.design/) - 企业级设计系统
- [Chakra UI](https://chakra-ui.com/) - 模块化组件库
- [Material-UI](https://mui.com/) - Google Material Design 实现

### 开发工具
- [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/) - Chrome 扩展
- [React Hook Form](https://react-hook-form.com/) - 表单处理库
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/) - 组件测试

## 🎯 下一步

完成本模块后，继续学习：
- [模块 3：Next.js 全栈应用](/modules/03-nextjs-fullstack/) - 学习全栈开发，升级为 V3.0 现代全栈网站

---

**学习提示**：组件化思维需要时间培养，从简单组件开始，逐步理解组件的设计原则和最佳实践！