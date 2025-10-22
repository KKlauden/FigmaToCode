---
layout: default
title: EP02：TypeScript基础 - 代码的类型安全保障
permalink: /modules/03-nextjs-fullstack/EP02-typescript-fundamentals/
---

# EP02: TypeScript基础 - 代码的类型安全保障 ⏱️ 55分钟

**🎧 EP02 配套播客**：
**🎵 TypeScript基础：代码的设计规范系统**

- [🎧 Internet Archive 收听](https://archive.org/details/03-ep-02-typescript-fundamentals) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/03-ep-02-typescript-fundamentals) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**代码的"设计规范"系统建立**：

- TypeScript基础类型系统和接口定义 📝
- Next.js项目的TypeScript配置优化 ⚙️
- React组件的类型化改造实践 ⚛️
- 高级类型简要介绍（作为拓展学习）🔍

**这55分钟将让你的代码拥有设计规范般的严谨性！** ✨

## 🤔 为什么要用TypeScript？（10分钟）

### JavaScript的"设计缺陷"

想象你在Figma中设计组件，但没有任何约束：

```javascript
// JavaScript: 没有约束的"设计"
function Button(props) {
  return (
    <button onClick={props.click}>
      {props.text}
    </button>
  )
}

// 使用时可能出现的问题：
<Button click="not-a-function" text={123} />  // 运行时才会出错
<Button text="Click me" />                     // 缺少onClick，静默失败
<Button onClick={handleClick} label="Click" /> // 错误的prop名称
```

### TypeScript的"设计规范"

```typescript
// TypeScript: 有约束的"设计规范"
interface ButtonProps {
  text: string
  onClick: () => void
  disabled?: boolean  // 可选属性
}

function Button({ text, onClick, disabled = false }: ButtonProps) {
  return (
    <button onClick={onClick} disabled={disabled}>
      {text}
    </button>
  )
}

// 使用时的类型检查：
<Button text="Click me" onClick={handleClick} />        // ✅ 正确
<Button text={123} onClick={handleClick} />             // ❌ 类型错误
<Button text="Click me" onClick="not-function" />       // ❌ 类型错误
<Button text="Click me" />                              // ❌ 缺少必需属性
```

### 设计师友好的理解

| 设计规范概念 | TypeScript概念 | 实际价值 |
|-------------|--------------|----------|
| 组件规范文档 | 接口定义(Interface) | 明确组件使用方式 |
| 设计约束 | 类型约束 | 防止错误使用 |
| 组件检查器 | 类型检查 | 实时发现问题 |
| 设计系统一致性 | 类型一致性 | 确保代码质量 |

**TypeScript = 代码的设计系统规范**

## 📝 TypeScript基础类型系统（15分钟）

### 基础类型

```typescript
// 1. 基本类型
let name: string = "Portfolio 2.0"
let age: number = 25
let isDesigner: boolean = true

// 2. 数组类型
let skills: string[] = ["UI设计", "React开发", "TypeScript"]
let scores: number[] = [90, 85, 95]

// 3. 对象类型
let designer: {
  name: string
  skills: string[]
  experience: number
} = {
  name: "张小明",
  skills: ["Figma", "React", "TypeScript"],
  experience: 3
}

// 4. 函数类型
function greet(name: string): string {
  return `Hello, ${name}!`
}

const calculateExperience = (startYear: number): number => {
  return new Date().getFullYear() - startYear
}
```

### 联合类型和字面量类型

```typescript
// 联合类型：多种可能的类型
type ButtonType = "primary" | "secondary" | "danger"
type Size = "small" | "medium" | "large"

// 使用联合类型
let buttonType: ButtonType = "primary"  // ✅
let buttonSize: Size = "medium"         // ✅
// let invalidType: ButtonType = "success" // ❌ 错误

// 对象中的联合类型
type ButtonConfig = {
  type: ButtonType
  size: Size
  disabled?: boolean  // 可选属性
}
```

### 接口定义

```typescript
// 定义组件Props接口
interface CardProps {
  title: string
  description: string
  imageUrl?: string        // 可选
  tags: string[]
  onViewDetails: () => void
}

// 定义数据结构接口
interface Project {
  id: number
  title: string
  description: string
  technologies: string[]
  imageUrl: string
  demoUrl?: string
  githubUrl?: string
  featured: boolean
}

// 接口继承
interface FeaturedProject extends Project {
  highlights: string[]
}
```

## ⚛️ React组件的TypeScript化（20分钟）

### 第一步：改造Navigation组件

将EP01的`app/components/Navigation.tsx`升级：

```tsx
'use client'

import Link from 'next/link'
import { usePathname } from 'next/navigation'

// 定义导航链接的类型
interface NavLink {
  href: string
  label: string
}

// 定义组件Props类型
interface NavigationProps {
  className?: string
}

export default function Navigation({ className = '' }: NavigationProps) {
  const pathname = usePathname()

  const links: NavLink[] = [
    { href: '/', label: '首页' },
    { href: '/about', label: '关于' },
    { href: '/projects', label: '项目' },
    { href: '/contact', label: '联系' },
  ]

  return (
    <nav className={`bg-white shadow-md ${className}`}>
      <div className="container mx-auto px-4">
        <div className="flex items-center justify-between h-16">
          <Link href="/" className="text-xl font-bold text-gray-900">
            Portfolio 2.0
          </Link>

          <div className="flex space-x-8">
            {links.map((link: NavLink) => (
              <Link
                key={link.href}
                href={link.href}
                className={`text-gray-600 hover:text-gray-900 transition-colors ${
                  pathname === link.href ? 'text-blue-600 font-medium' : ''
                }`}
              >
                {link.label}
              </Link>
            ))}
          </div>
        </div>
      </div>
    </nav>
  )
}
```

### 第二步：创建类型安全的Button组件

`app/components/ui/Button.tsx`：

```tsx
import { ReactNode, ButtonHTMLAttributes } from 'react'

// 定义按钮类型
type ButtonVariant = 'primary' | 'secondary' | 'outline' | 'ghost'
type ButtonSize = 'sm' | 'md' | 'lg'

// 继承原生button属性，同时添加自定义props
interface ButtonProps extends ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: ButtonVariant
  size?: ButtonSize
  children: ReactNode
  isLoading?: boolean
}

export default function Button({
  variant = 'primary',
  size = 'md',
  children,
  isLoading = false,
  className = '',
  disabled,
  ...rest
}: ButtonProps) {
  const baseClasses = 'inline-flex items-center justify-center font-medium rounded-md transition-colors focus:outline-none focus:ring-2 focus:ring-offset-2'

  const variantClasses = {
    primary: 'bg-blue-600 text-white hover:bg-blue-700 focus:ring-blue-500',
    secondary: 'bg-gray-600 text-white hover:bg-gray-700 focus:ring-gray-500',
    outline: 'border border-gray-300 text-gray-700 hover:bg-gray-50 focus:ring-blue-500',
    ghost: 'text-gray-600 hover:text-gray-900 hover:bg-gray-100 focus:ring-blue-500'
  }

  const sizeClasses = {
    sm: 'px-3 py-1.5 text-sm',
    md: 'px-4 py-2 text-base',
    lg: 'px-6 py-3 text-lg'
  }

  const isDisabled = disabled || isLoading

  return (
    <button
      className={`
        ${baseClasses}
        ${variantClasses[variant]}
        ${sizeClasses[size]}
        ${isDisabled ? 'opacity-50 cursor-not-allowed' : ''}
        ${className}
      `}
      disabled={isDisabled}
      {...rest}
    >
      {isLoading ? (
        <>
          <svg className="animate-spin -ml-1 mr-2 h-4 w-4" viewBox="0 0 24 24">
            <circle className="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" strokeWidth="4" fill="none" />
            <path className="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z" />
          </svg>
          加载中...
        </>
      ) : (
        children
      )}
    </button>
  )
}
```

### 第三步：创建类型安全的Card组件

`app/components/ui/Card.tsx`：

```tsx
import { ReactNode } from 'react'

interface CardProps {
  title?: string
  children: ReactNode
  className?: string
  shadow?: 'none' | 'sm' | 'md' | 'lg'
  padding?: 'none' | 'sm' | 'md' | 'lg'
}

export default function Card({
  title,
  children,
  className = '',
  shadow = 'md',
  padding = 'md'
}: CardProps) {
  const shadowClasses = {
    none: '',
    sm: 'shadow-sm',
    md: 'shadow-md',
    lg: 'shadow-lg'
  }

  const paddingClasses = {
    none: '',
    sm: 'p-4',
    md: 'p-6',
    lg: 'p-8'
  }

  return (
    <div className={`
      bg-white rounded-lg border border-gray-200
      ${shadowClasses[shadow]}
      ${paddingClasses[padding]}
      ${className}
    `}>
      {title && (
        <h3 className="text-lg font-semibold text-gray-900 mb-4">
          {title}
        </h3>
      )}
      {children}
    </div>
  )
}
```

### 第四步：使用类型安全组件

更新 `app/projects/page.tsx`：

```tsx
import Button from '../components/ui/Button'
import Card from '../components/ui/Card'

// 定义项目数据类型
interface Project {
  id: number
  title: string
  description: string
  technologies: string[]
  demoUrl?: string
  githubUrl?: string
}

export default function Projects() {
  const projects: Project[] = [
    {
      id: 1,
      title: 'Portfolio 1.0',
      description: '使用HTML/CSS构建的个人作品集，响应式设计，包含项目展示和联系方式。',
      technologies: ['HTML', 'CSS', 'JavaScript'],
      demoUrl: 'https://example.com',
      githubUrl: 'https://github.com/example'
    },
    {
      id: 2,
      title: 'React组件库',
      description: '可复用的React组件集合，包含Button、Card、Form等常用组件。',
      technologies: ['React', 'TypeScript', 'Storybook'],
      githubUrl: 'https://github.com/example'
    },
    {
      id: 3,
      title: 'Portfolio 2.0',
      description: '使用Next.js + TypeScript + Tailwind CSS构建的现代化作品集。',
      technologies: ['Next.js', 'TypeScript', 'Tailwind CSS'],
      demoUrl: 'https://example.com'
    }
  ]

  const handleViewDemo = (url: string) => {
    window.open(url, '_blank')
  }

  const handleViewCode = (url: string) => {
    window.open(url, '_blank')
  }

  return (
    <main className="min-h-screen bg-gradient-to-br from-green-50 to-emerald-100">
      <div className="container mx-auto px-4 py-16">
        <h1 className="text-4xl font-bold text-gray-900 mb-8">
          我的项目
        </h1>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {projects.map((project: Project) => (
            <Card key={project.id} shadow="lg">
              <h3 className="text-xl font-semibold mb-4">{project.title}</h3>
              <p className="text-gray-600 mb-4">{project.description}</p>

              <div className="mb-4">
                <h4 className="text-sm font-medium text-gray-700 mb-2">技术栈：</h4>
                <div className="flex flex-wrap gap-2">
                  {project.technologies.map((tech: string) => (
                    <span
                      key={tech}
                      className="px-2 py-1 bg-blue-100 text-blue-800 text-xs rounded-full"
                    >
                      {tech}
                    </span>
                  ))}
                </div>
              </div>

              <div className="flex gap-2">
                {project.demoUrl && (
                  <Button
                    size="sm"
                    onClick={() => handleViewDemo(project.demoUrl!)}
                  >
                    查看演示
                  </Button>
                )}
                {project.githubUrl && (
                  <Button
                    variant="outline"
                    size="sm"
                    onClick={() => handleViewCode(project.githubUrl!)}
                  >
                    查看代码
                  </Button>
                )}
              </div>
            </Card>
          ))}
        </div>
      </div>
    </main>
  )
}
```

## 🔧 TypeScript配置优化（5分钟）

### 严格类型检查

更新 `tsconfig.json`：

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "es6"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [
      {
        "name": "next"
      }
    ],
    "paths": {
      "@/*": ["./*"],
      "@/components/*": ["./app/components/*"],
      "@/ui/*": ["./app/components/ui/*"]
    },
    // 启用严格检查
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
```

### 创建全局类型定义

`app/types/global.ts`：

```typescript
// 全局类型定义
export interface User {
  id: string
  name: string
  email: string
  avatar?: string
}

export interface Project {
  id: number
  title: string
  description: string
  technologies: string[]
  imageUrl?: string
  demoUrl?: string
  githubUrl?: string
  featured: boolean
  createdAt: string
}

export interface Skill {
  name: string
  level: 'beginner' | 'intermediate' | 'advanced' | 'expert'
  category: 'design' | 'frontend' | 'backend' | 'tools'
}

export interface ContactForm {
  name: string
  email: string
  subject: string
  message: string
}

// API 响应类型
export interface ApiResponse<T> {
  data: T
  message: string
  success: boolean
}

// 组件通用Props类型
export interface BaseProps {
  className?: string
  children?: React.ReactNode
}
```

## 🎓 高级类型简要介绍（5分钟）

### 作为拓展学习的高级概念

```typescript
// 1. 泛型 (Generics) - 可复用的类型
interface ApiResponse<T> {
  data: T
  status: number
  message: string
}

const userResponse: ApiResponse<User> = {
  data: { id: '1', name: 'John', email: 'john@example.com' },
  status: 200,
  message: 'Success'
}

// 2. 实用类型 (Utility Types)
type PartialUser = Partial<User>        // 所有属性变为可选
type RequiredUser = Required<User>      // 所有属性变为必需
type UserEmail = Pick<User, 'email'>    // 只选择email属性
type UserWithoutId = Omit<User, 'id'>   // 排除id属性

// 3. 条件类型 (Conditional Types) - 高级概念
type NonNullable<T> = T extends null | undefined ? never : T

// 4. 映射类型 (Mapped Types) - 高级概念
type ReadonlyUser = {
  readonly [K in keyof User]: User[K]
}
```

**这些高级概念建议在掌握基础后再深入学习。**

## 🤖 AI协作：TypeScript问题解决

在Codex中尝试这些对话：

1. **类型定义问题**
   ```
   "这个React组件的Props应该怎么定义TypeScript接口？"
   ```

2. **类型错误处理**
   ```
   "TypeScript报错'Property does not exist'怎么解决？"
   ```

3. **泛型使用**
   ```
   "如何为这个API响应函数定义泛型类型？"
   ```

4. **类型导入导出**
   ```
   "TypeScript项目中如何组织和管理类型定义文件？"
   ```

## 🎯 完成检查

- [ ] 理解TypeScript的基础类型系统
- [ ] 成功定义接口和联合类型
- [ ] 完成React组件的TypeScript化改造
- [ ] 创建了类型安全的Button和Card组件
- [ ] 配置了严格的TypeScript检查
- [ ] 建立了全局类型定义文件
- [ ] 理解了高级类型的基本概念
- [ ] 体验了TypeScript的开发时错误检查

## 🚀 恭喜你！

**你刚刚为代码建立了"设计规范"系统！** 🎉

现在你知道了：
- 📝 TypeScript为代码提供了设计规范般的约束
- 🛡️ 类型检查能在开发时发现潜在问题
- ⚛️ React组件可以通过TypeScript获得更好的开发体验
- 🔧 接口定义让组件使用更加清晰和安全
- 🎯 严格类型检查提升了代码质量

**Portfolio 2.0现在拥有了完整的类型安全保障！**

你的代码现在就像有了设计系统规范的设计稿一样，清晰、一致、可靠。

## 🎯 下一步

现在你的项目有了类型安全保障，是时候添加现代化的样式系统了！

继续学习：[EP03: Tailwind CSS + 主题定制 - 设计系统实现](../EP03-tailwind-design-system/) - 为Portfolio 2.0构建完整的设计系统

---

**代码设计规范的价值**：TypeScript就像代码的设计系统，它确保每个组件的使用都符合"设计规范"，减少错误，提升可维护性。现在你具备了企业级TypeScript开发的基础能力！🎨→📝→🛡️→✨