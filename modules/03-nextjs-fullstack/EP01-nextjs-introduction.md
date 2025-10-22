---
layout: default
title: EP01：Next.js入门 - 现代化React框架
permalink: /modules/03-nextjs-fullstack/EP01-nextjs-introduction/
---

# EP01: Next.js入门 - 现代化React框架 ⏱️ 50分钟

**🎧 EP01 配套播客**：
**🎵 Next.js入门：现代化React框架的设计师友好体验**

- [🎧 Internet Archive 收听](https://archive.org/details/03-ep-01-nextjs-introduction) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/03-ep-01-nextjs-introduction) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**从React到全栈框架的升级**：

- Next.js vs Create React App的根本差异理解 🆚
- App Router的文件系统路由概念掌握 📁
- Portfolio 2.0项目创建和基础架构搭建 🏗️
- 体验现代化React开发框架的威力 ⚡

**这50分钟将让你进入现代化React开发的世界！** ✨

## 🤔 为什么要学Next.js？（10分钟）

### React的局限性

回顾模块02的React项目，你可能遇到过这些问题：

**路由管理复杂**：
```jsx
// React Router需要手动配置
import { BrowserRouter, Routes, Route } from 'react-router-dom'

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/projects" element={<Projects />} />
      </Routes>
    </BrowserRouter>
  )
}
```

**性能优化困难**：
- 图片需要手动优化
- 字体加载需要额外配置
- SEO优化需要复杂设置

**部署配置复杂**：
- 需要手动配置构建流程
- 服务端渲染需要复杂架构

### Next.js的解决方案

**文件系统路由**：
```
app/
├── page.tsx          # / 路由
├── about/
│   └── page.tsx      # /about 路由
└── projects/
    └── page.tsx      # /projects 路由
```

**内置优化**：
- 自动图片优化
- 智能字体加载
- 自动代码分割

**一键部署**：
- Vercel零配置部署
- 自动HTTPS和CDN

### 设计师友好的理解

| 设计工具体验 | Next.js体验 | 价值 |
|-------------|------------|-----|
| Figma页面管理 | 文件系统路由 | 直观的项目结构 |
| 自动保存 | 热更新 | 即时反馈 |
| 组件库管理 | 内置优化 | 专注设计而非配置 |
| 一键分享 | 一键部署 | 快速展示作品 |

## 🛠 Next.js项目创建：Portfolio 2.0（15分钟）

### 第一步：创建Next.js项目

```bash
# 创建新的Next.js项目
npx create-next-app@latest portfolio-v2

# 在创建过程中的选择：
✅ Would you like to use TypeScript? → Yes
✅ Would you like to use ESLint? → Yes
✅ Would you like to use Tailwind CSS? → Yes
✅ Would you like to use `src/` directory? → No
✅ Would you like to use App Router? → Yes
✅ Would you like to customize the default import alias? → No
```

```bash
# 进入项目目录
cd portfolio-v2

# 启动开发服务器
npm run dev
```

访问 `http://localhost:3000`，你会看到Next.js的欢迎页面！

### 第二步：理解Next.js项目结构

```
portfolio-v2/
├── app/                    # App Router 核心目录
│   ├── globals.css         # 全局样式
│   ├── layout.tsx          # 根布局组件
│   ├── page.tsx           # 首页组件
│   └── favicon.ico        # 网站图标
├── public/                # 静态资源
├── next.config.js         # Next.js配置
├── tailwind.config.js     # Tailwind配置
└── package.json           # 项目配置
```

**核心概念理解**：
- `app/` = 你的网站结构，就像Figma的页面层级
- `layout.tsx` = 网站的整体框架，类似设计稿的母版页
- `page.tsx` = 具体页面内容，类似单个设计页面
- `globals.css` = 全局样式规范，类似设计系统的基础变量

### 第三步：清理默认内容

**替换 `app/page.tsx`**：
```tsx
export default function Home() {
  return (
    <main className="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100">
      <div className="container mx-auto px-4 py-16">
        <div className="text-center">
          <h1 className="text-4xl font-bold text-gray-900 mb-4">
            Portfolio 2.0
          </h1>
          <p className="text-xl text-gray-600 mb-8">
            现代化React开发工具实践
          </p>
          <p className="text-lg text-gray-500">
            Next.js + TypeScript + Tailwind CSS
          </p>
        </div>
      </div>
    </main>
  )
}
```

**更新 `app/layout.tsx`**：
```tsx
import type { Metadata } from 'next'
import { Inter } from 'next/font/google'
import './globals.css'

const inter = Inter({ subsets: ['latin'] })

export const metadata: Metadata = {
  title: 'Portfolio 2.0 - 现代化作品集',
  description: '使用Next.js + TypeScript + Tailwind CSS构建的现代化个人作品集',
}

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="zh-CN">
      <body className={inter.className}>{children}</body>
    </html>
  )
}
```

保存文件，查看页面变化！🎉

## 📁 App Router：文件系统路由（15分钟）

### 理解文件系统路由

**传统路由 vs App Router**：

```
// 传统方式（React Router）
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
  <Route path="/projects" element={<Projects />} />
  <Route path="/contact" element={<Contact />} />
</Routes>

// Next.js App Router 方式
app/
├── page.tsx              # /
├── about/page.tsx        # /about
├── projects/page.tsx     # /projects
└── contact/page.tsx      # /contact
```

### 创建Portfolio 2.0的页面结构

**创建关于页面**：
```bash
mkdir app/about
```

`app/about/page.tsx`：
```tsx
export default function About() {
  return (
    <main className="min-h-screen bg-gradient-to-br from-purple-50 to-pink-100">
      <div className="container mx-auto px-4 py-16">
        <h1 className="text-4xl font-bold text-gray-900 mb-8">
          关于我
        </h1>
        <div className="max-w-2xl">
          <p className="text-lg text-gray-600 mb-6">
            我是一名UI/UX设计师，正在学习现代化React开发技术。
          </p>
          <p className="text-lg text-gray-600">
            通过FigmaToCode课程，我掌握了Next.js、TypeScript和Tailwind CSS等现代化工具。
          </p>
        </div>
      </div>
    </main>
  )
}
```

**创建项目页面**：
```bash
mkdir app/projects
```

`app/projects/page.tsx`：
```tsx
export default function Projects() {
  return (
    <main className="min-h-screen bg-gradient-to-br from-green-50 to-emerald-100">
      <div className="container mx-auto px-4 py-16">
        <h1 className="text-4xl font-bold text-gray-900 mb-8">
          我的项目
        </h1>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div className="bg-white rounded-lg shadow-md p-6">
            <h3 className="text-xl font-semibold mb-4">Portfolio 1.0</h3>
            <p className="text-gray-600">使用HTML/CSS构建的个人作品集</p>
          </div>
          <div className="bg-white rounded-lg shadow-md p-6">
            <h3 className="text-xl font-semibold mb-4">React组件库</h3>
            <p className="text-gray-600">可复用的React组件集合</p>
          </div>
          <div className="bg-white rounded-lg shadow-md p-6">
            <h3 className="text-xl font-semibold mb-4">Portfolio 2.0</h3>
            <p className="text-gray-600">现代化工具链构建的作品集</p>
          </div>
        </div>
      </div>
    </main>
  )
}
```

**创建联系页面**：
```bash
mkdir app/contact
```

`app/contact/page.tsx`：
```tsx
export default function Contact() {
  return (
    <main className="min-h-screen bg-gradient-to-br from-orange-50 to-red-100">
      <div className="container mx-auto px-4 py-16">
        <h1 className="text-4xl font-bold text-gray-900 mb-8">
          联系我
        </h1>
        <div className="max-w-md">
          <div className="space-y-4">
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">
                邮箱
              </label>
              <p className="text-gray-600">hello@portfolio.com</p>
            </div>
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">
                GitHub
              </label>
              <p className="text-gray-600">github.com/your-username</p>
            </div>
            <div>
              <label className="block text-sm font-medium text-gray-700 mb-2">
                LinkedIn
              </label>
              <p className="text-gray-600">linkedin.com/in/your-profile</p>
            </div>
          </div>
        </div>
      </div>
    </main>
  )
}
```

现在试试访问：
- `http://localhost:3000/` - 首页
- `http://localhost:3000/about` - 关于页面
- `http://localhost:3000/projects` - 项目页面
- `http://localhost:3000/contact` - 联系页面

**🎉 成功！** 你刚刚创建了一个完整的多页面Next.js应用！

## 🧭 添加导航组件（10分钟）

### 创建导航组件

`app/components/Navigation.tsx`：
```tsx
'use client'

import Link from 'next/link'
import { usePathname } from 'next/navigation'

export default function Navigation() {
  const pathname = usePathname()

  const links = [
    { href: '/', label: '首页' },
    { href: '/about', label: '关于' },
    { href: '/projects', label: '项目' },
    { href: '/contact', label: '联系' },
  ]

  return (
    <nav className="bg-white shadow-md">
      <div className="container mx-auto px-4">
        <div className="flex items-center justify-between h-16">
          <Link href="/" className="text-xl font-bold text-gray-900">
            Portfolio 2.0
          </Link>

          <div className="flex space-x-8">
            {links.map((link) => (
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

### 在布局中添加导航

更新 `app/layout.tsx`：
```tsx
import type { Metadata } from 'next'
import { Inter } from 'next/font/google'
import './globals.css'
import Navigation from './components/Navigation'

const inter = Inter({ subsets: ['latin'] })

export const metadata: Metadata = {
  title: 'Portfolio 2.0 - 现代化作品集',
  description: '使用Next.js + TypeScript + Tailwind CSS构建的现代化个人作品集',
}

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="zh-CN">
      <body className={inter.className}>
        <Navigation />
        {children}
      </body>
    </html>
  )
}
```

现在你的网站有了完整的导航系统！点击不同的链接，观察URL变化和页面切换。

## 🤖 AI协作：Next.js开发技巧

在Codex中尝试这些对话：

1. **理解Next.js优势**
   ```
   "相比传统React项目，Next.js在哪些方面提升了开发体验？"
   ```

2. **App Router概念**
   ```
   "App Router的文件系统路由如何工作？如何创建嵌套路由？"
   ```

3. **性能优化**
   ```
   "Next.js有哪些内置的性能优化特性？"
   ```

4. **项目架构**
   ```
   "如何组织大型Next.js项目的文件结构？"
   ```

## 🎯 完成检查

- [ ] 成功创建Next.js项目并启动开发服务器
- [ ] 理解App Router的文件系统路由概念
- [ ] 创建了Portfolio 2.0的基础页面结构
- [ ] 实现了完整的导航系统
- [ ] 体验了Next.js的热更新和开发体验
- [ ] 理解了Next.js相比传统React的优势
- [ ] 掌握了`use client`指令的使用场景
- [ ] 建立了"文件结构=网站结构"的思维

## 🚀 恭喜你！

**你刚刚完成了从React到Next.js的重要升级！** 🎉

现在你知道了：
- 🏗️ Next.js提供了更现代化的React开发体验
- 📁 文件系统路由让项目组织变得直观
- ⚡ 内置优化让网站性能自然而然地提升
- 🧭 App Router让多页面应用开发变得简单
- 🔧 现代化工具链减少了配置复杂度

**Portfolio 2.0的基础架构已经搭建完成！**

接下来你将学习TypeScript，为这个项目添加类型安全保障，让代码更加可靠和可维护。

## 🎯 下一步

现在你有了现代化的Next.js项目基础，是时候添加类型安全保障了！

继续学习：[EP02: TypeScript基础 - 代码的类型安全保障](../EP02-typescript-fundamentals/) - 为Portfolio 2.0添加TypeScript类型系统

---

**设计师的现代化工具体验**：文件系统路由就像Figma的页面管理一样直观，Next.js让React开发变得更加设计师友好。现在你具备了现代化全栈开发的基础能力！🎨→⚛️→🚀→✨