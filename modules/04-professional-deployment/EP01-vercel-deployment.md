---
layout: default
title: EP01：Vercel一键部署 - 最简单的上线体验
permalink: /modules/04-professional-deployment/EP01-vercel-deployment/
---

# EP01: Vercel一键部署 - 最简单的上线体验 ⏱️ 40分钟

**🎧 EP01 配套播客**：
**🎵 Vercel一键部署：现代化部署的设计师友好体验**

- [🎧 Internet Archive 收听](https://archive.org/details/04-ep-01-vercel-deployment) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/04-ep-01-vercel-deployment) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**从本地开发到在线展示的零配置体验**：

- Portfolio 2.0项目的GitHub仓库准备和推送 🚀
- Vercel平台注册和项目连接配置 🔗
- 自动化部署流程体验和监控理解 📊
- 预览环境vs生产环境的实际应用场景 🌐

**这40分钟将让你体验现代化部署的便利性，获得第一个在线作品集！** ✨

## 🤔 为什么选择Vercel？（8分钟）

### 现代化部署的设计师理解

**传统部署 vs Vercel部署**：

传统方式：
```
购买服务器 → 配置环境 → 上传代码 → 配置域名 → 手动更新
```

Vercel方式：
```
GitHub推送 → 自动部署 ✓
```

### Vercel的设计师友好特性

| 设计工具体验 | Vercel体验 | 价值 |
|-------------|------------|------|
| Figma一键分享 | 一键部署 | 即时展示作品 |
| 设计稿版本管理 | 自动化部署 | 每次更新自动上线 |
| 预览模式 | 预览链接 | 安全的内容预览 |
| 发布状态 | 部署状态 | 实时了解发布进度 |

### Next.js + Vercel的完美组合

**同一团队开发**：
- Vercel公司同时开发Next.js和Vercel平台
- 零配置集成，无需复杂设置
- 性能优化自动启用

**自动化优势**：
- 代码推送即部署
- HTTPS自动配置
- CDN全球加速
- 性能监控内置

## 📚 第一步：准备GitHub仓库（10分钟）

### 检查Portfolio 2.0项目状态

确保你的Portfolio 2.0项目已完成：

```bash
# 检查项目结构
ls -la portfolio-v2/
```

应该看到：
```
portfolio-v2/
├── app/
├── components/
├── public/
├── package.json
├── next.config.js
├── tailwind.config.js
└── tsconfig.json
```

### 本地测试确认

```bash
# 进入项目目录
cd portfolio-v2

# 安装依赖
npm install

# 本地构建测试
npm run build

# 启动项目
npm run dev
```

访问 `http://localhost:3000` 确认项目正常运行。

### 创建GitHub仓库

**方法一：GitHub网站创建**

1. 访问 [GitHub.com](https://github.com)
2. 点击右上角 "+" → "New repository"
3. 仓库名称：`portfolio-v2`
4. 描述：`Modern portfolio built with Next.js + TypeScript + Tailwind CSS`
5. 设置为 **Public**（重要：Vercel免费版需要公开仓库）
6. 不要初始化README（我们已有项目）

**方法二：GitHub CLI创建**

```bash
# 安装GitHub CLI（如果未安装）
# macOS: brew install gh
# Windows: winget install GitHub.cli

# 登录GitHub
gh auth login

# 创建远程仓库
gh repo create portfolio-v2 --public --description "Modern portfolio built with Next.js + TypeScript + Tailwind CSS"
```

### 推送代码到GitHub

```bash
# 初始化Git（如果未初始化）
git init

# 添加所有文件
git add .

# 首次提交
git commit -m "Initial commit: Portfolio 2.0 with Next.js + TypeScript + Tailwind CSS

🎨 Features:
- Modern Next.js App Router architecture
- TypeScript for type safety
- Tailwind CSS design system
- Responsive navigation and pages
- Custom theme configuration

🚀 Ready for deployment with Vercel"

# 添加远程仓库
git remote add origin https://github.com/YOUR_USERNAME/portfolio-v2.git

# 推送到GitHub
git push -u origin main
```

**🎉 成功标志**：在GitHub上看到你的Portfolio 2.0代码！

## 🚀 第二步：Vercel平台配置（15分钟）

### 注册Vercel账号

1. **访问Vercel官网**：https://vercel.com
2. **选择注册方式**：推荐使用GitHub账号登录
3. **GitHub授权**：允许Vercel访问你的GitHub仓库

### 导入项目

**在Vercel Dashboard中**：

1. **点击 "Add New..."** → "Project"
2. **选择GitHub仓库**：找到 `portfolio-v2`
3. **导入项目**：点击 "Import"

### 项目配置（重要）

Vercel会自动检测到Next.js项目，但确认以下配置：

**Framework Preset**: Next.js ✓
**Root Directory**: `./` ✓
**Build Command**:
```bash
npm run build
```

**Install Command**:
```bash
npm install
```

**Output Directory**:
```
.next
```

### 环境变量配置（如需要）

如果你的项目使用环境变量，在 "Environment Variables" 部分添加：

```
NODE_ENV=production
NEXT_PUBLIC_SITE_URL=https://your-project.vercel.app
```

### 部署启动

点击 **"Deploy"** 开始第一次部署！

**部署过程监控**：
- 📦 Building... （构建阶段）
- 🚀 Deploying... （部署阶段）
- ✅ Ready! （完成）

**预计时间**：2-5分钟

## 🔍 第三步：理解部署结果（7分钟）

### 部署成功页面分析

部署完成后，你会看到：

**🎉 Deployment Successful**

关键信息：
- **Production URL**: `https://portfolio-v2-username.vercel.app`
- **Deployment ID**: 每次部署的唯一标识
- **Build Time**: 构建耗时
- **Deployment Time**: 总部署时间

### 预览你的在线作品集

**点击访问链接**，你应该看到：
- ✅ 完整的Portfolio 2.0网站
- ✅ 所有页面正常加载
- ✅ 导航功能正常
- ✅ Tailwind样式正确显示
- ✅ TypeScript编译成功

### 理解Vercel提供的URLs

**Production URL**:
- 格式：`https://project-name-username.vercel.app`
- 用途：正式的生产环境地址

**Branch URLs**:
- 格式：`https://project-name-git-branch-username.vercel.app`
- 用途：每个Git分支的独立预览

**Deployment URLs**:
- 格式：`https://project-name-hash.vercel.app`
- 用途：每次部署的永久链接

### 性能分析初探

在Vercel Dashboard中查看：
- **Core Web Vitals**: 页面性能指标
- **Function Logs**: 服务端日志（如有）
- **Bandwidth Usage**: 流量使用情况

## 📊 第四步：自动化部署体验（5分钟）

### 测试自动化部署

让我们体验代码更新的自动部署：

1. **修改页面内容**：

编辑 `app/page.tsx`：
```tsx
export default function Home() {
  return (
    <main className="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100">
      <div className="container mx-auto px-4 py-16">
        <div className="text-center">
          <h1 className="text-4xl font-bold text-gray-900 mb-4">
            Portfolio 2.0 - Now Live! 🚀
          </h1>
          <p className="text-xl text-gray-600 mb-8">
            现代化React开发工具实践 - 已成功部署
          </p>
          <p className="text-lg text-gray-500">
            Next.js + TypeScript + Tailwind CSS
          </p>
          <div className="mt-8 p-4 bg-green-100 rounded-lg inline-block">
            <p className="text-green-800 font-medium">
              ✅ 自动化部署测试成功！
            </p>
            <p className="text-green-600 text-sm mt-1">
              每次Git推送都会触发自动部署
            </p>
          </div>
        </div>
      </div>
    </main>
  )
}
```

2. **提交并推送**：

```bash
git add .
git commit -m "feat: add deployment success notification

🎉 Update home page to celebrate successful Vercel deployment
✨ Add visual feedback for automatic deployment testing"

git push origin main
```

3. **观察自动化部署**：

- 访问Vercel Dashboard
- 看到新的部署开始
- 实时监控构建和部署过程
- 部署完成后自动更新生产环境

**🎉 成功标志**：网站内容自动更新！

## 🧭 预览环境 vs 生产环境（5分钟）

### 预览环境的作用

**创建功能分支测试**：

```bash
# 创建新分支
git checkout -b feature/contact-form

# 修改contact页面
# 编辑 app/contact/page.tsx，添加一些测试内容

git add .
git commit -m "feat: enhance contact page with form elements"
git push origin feature/contact-form
```

**结果**：
- Vercel自动为分支创建预览环境
- 预览URL：`https://portfolio-v2-git-feature-contact-form-username.vercel.app`
- 生产环境保持不变

### 预览环境的价值

**设计师的理解方式**：
- 预览环境 = Figma的分享链接，用于收集反馈
- 生产环境 = 正式发布的设计稿，面向最终用户

**实际应用场景**：
- 功能开发和测试
- 团队协作和反馈收集
- 客户预览和确认
- A/B测试和实验

## 🤖 AI协作：Vercel部署优化

在Codex中尝试这些对话：

1. **部署问题排查**
   ```
   "Vercel部署失败，构建日志显示TypeScript错误，如何解决？"
   ```

2. **性能优化建议**
   ```
   "如何优化Next.js项目的Vercel部署性能？"
   ```

3. **环境变量配置**
   ```
   "在Vercel中如何正确配置Next.js的环境变量？"
   ```

4. **域名配置准备**
   ```
   "准备为Vercel项目配置自定义域名，需要了解哪些概念？"
   ```

## 🎯 完成检查

- [ ] 成功创建GitHub仓库并推送Portfolio 2.0代码
- [ ] 注册Vercel账号并连接GitHub
- [ ] 完成项目导入和首次部署
- [ ] 获得可访问的在线作品集URL
- [ ] 体验自动化部署流程
- [ ] 理解预览环境和生产环境的区别
- [ ] 掌握Vercel Dashboard的基本功能
- [ ] 建立代码推送→自动部署的工作流

## 🚀 恭喜你！

**你已经拥有了第一个在线作品集网站！** 🎉

现在你掌握了：
- 🌐 现代化部署平台的使用方法
- 🔄 自动化部署的工作流程
- 📊 部署状态和性能的基础监控
- 🚀 零配置上线的便利体验
- 💼 可以直接展示给雇主的在线作品

**Portfolio 2.0已经成功上线，全世界都能访问你的作品了！**

你的网站现在具备：
- ✅ HTTPS安全连接
- ✅ 全球CDN加速
- ✅ 自动化部署更新
- ✅ 移动端完美适配
- ✅ 专业的性能优化

## 🎯 下一步

现在你的作品集已经在线，是时候让它更加专业化了！

继续学习：[EP02: 自定义域名和生产优化](../EP02-custom-domain-optimization/) - 为你的作品集配置专业域名，建立个人品牌形象

---

**现代化部署的威力**：从代码推送到全球可访问，仅需几分钟。Vercel让部署变得像Figma分享设计稿一样简单，这就是现代化工具的魅力！现在你体验到了什么叫"开发者体验优先"的平台设计。🎨→💻→🌐→✨

## 📚 常见问题解决

### 部署失败常见原因

**1. TypeScript编译错误**
```bash
# 本地检查TypeScript
npm run type-check
```

**2. 构建错误**
```bash
# 本地测试构建
npm run build
```

**3. 依赖问题**
```bash
# 清理并重新安装
rm -rf node_modules package-lock.json
npm install
```

### Vercel限制说明

**免费版限制**：
- 100GB带宽/月
- 1000次函数调用/天
- 仅支持公开GitHub仓库

**足够个人作品集使用**，无需担心超限。