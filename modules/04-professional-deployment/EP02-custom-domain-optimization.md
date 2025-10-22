---
layout: default
title: EP02：自定义域名和生产优化 - 个人品牌网站实现
permalink: /modules/04-professional-deployment/EP02-custom-domain-optimization/
---

# EP02: 自定义域名和生产优化 - 个人品牌网站实现 ⏱️ 45分钟

**🎧 EP02 配套播客**：
**🎵 域名配置与生产优化：个人品牌网站的专业化实现**

- [🎧 Internet Archive 收听](https://archive.org/details/04-ep-02-custom-domain-optimization) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/04-ep-02-custom-domain-optimization) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**从通用URL到专业品牌域名的升级**：

- 域名购买指导和服务商选择（国内外对比）🌐
- DNS配置和域名解析设置详解 🔧
- HTTPS自动配置和安全保障机制 🔒
- 基础SEO优化和搜索引擎收录配置 📈

**这45分钟将让你拥有一个真正专业的个人品牌网站！** ✨

## 🤔 为什么需要自定义域名？（8分钟）

### 品牌形象的重要性

**免费域名 vs 自定义域名**：

```
免费域名：https://portfolio-v2-username.vercel.app
自定义域名：https://yourname.com
```

### 设计师视角的域名价值

| 设计概念 | 域名概念 | 品牌价值 |
|----------|----------|----------|
| 品牌标识 | 域名地址 | 专业形象建立 |
| 设计一致性 | 品牌域名 | 记忆点强化 |
| 作品署名 | 域名所有权 | 个人品牌资产 |
| 客户信任 | 专业域名 | 可信度提升 |

### 实际应用场景

**职业发展**：
- 简历上的专业网站地址
- 名片和社交媒体的统一品牌
- 客户和雇主的第一印象

**SEO优势**：
- 搜索引擎收录更好
- 社交媒体分享更专业
- 品牌搜索结果优化

## 🌐 第一步：域名购买指导（12分钟）

### 域名服务商选择

#### 🇨🇳 国内域名服务商

**阿里云（万网）**：
- **优势**：中文服务，支付便捷，备案支持
- **价格**：.com域名 ¥55-65/年
- **适合**：主要面向国内用户的网站
- **购买链接**：https://wanwang.aliyun.com

**腾讯云**：
- **优势**：企业级服务，与云服务器集成
- **价格**：.com域名 ¥55-69/年
- **适合**：计划使用腾讯云服务的用户
- **购买链接**：https://dnspod.cloud.tencent.com

#### 🌍 国外域名服务商

**Namecheap**：
- **优势**：价格便宜，隐私保护免费
- **价格**：.com域名 $8-12/年
- **适合**：国际化网站，隐私要求高
- **购买链接**：https://www.namecheap.com

**Google Domains**：
- **优势**：Google生态集成，DNS管理简单
- **价格**：.com域名 $12/年
- **适合**：使用Google服务多的用户
- **购买链接**：https://domains.google.com

**Cloudflare Registrar**：
- **优势**：成本价售卖，免费DNS和CDN
- **价格**：.com域名 $8.57/年（成本价）
- **适合**：技术用户，性价比最高
- **购买链接**：https://www.cloudflare.com/products/registrar/

### 域名选择建议

**个人品牌域名策略**：

1. **首选方案**：`yourname.com`
   - 例如：`zhangwei.com`, `lihua.com`

2. **备选方案**：
   - `yourname.design` - 突出设计师身份
   - `yourname.dev` - 突出开发者身份
   - `yourname.io` - 技术感更强

3. **创意方案**：
   - `your-name.com`（中划线连接）
   - `iamyourname.com`
   - `yourname.studio`

### 域名购买演示（以Namecheap为例）

**第一步：搜索域名**
1. 访问 Namecheap.com
2. 搜索你想要的域名
3. 检查可用性和价格

**第二步：添加隐私保护**
```
Domain Privacy Protection: ✅ 免费
WhoisGuard: ✅ 推荐开启
```

**第三步：选择DNS服务**
```
Namecheap BasicDNS: ✅ 免费（基础使用）
Cloudflare DNS: ✅ 推荐（更好性能）
```

**第四步：完成购买**
- 创建账号
- 填写真实联系信息
- 选择支付方式
- 确认购买

**🎉 成功标志**：收到域名购买确认邮件！

## 🔧 第二步：DNS配置和Vercel连接（15分钟）

### 理解DNS的作用

**DNS就像地址簿**：
```
域名(yourname.com) → DNS解析 → IP地址(Vercel服务器)
```

**设计师的理解**：
- 域名 = 品牌名称
- DNS = 地址指向
- IP地址 = 实际位置

### 在Vercel中添加自定义域名

**第一步：进入Vercel项目设置**
1. 打开Vercel Dashboard
2. 选择你的Portfolio 2.0项目
3. 点击 "Settings" 标签
4. 选择 "Domains" 选项

**第二步：添加域名**
1. 在 "Add Domain" 输入框中输入：`yourname.com`
2. 点击 "Add"
3. Vercel会显示需要配置的DNS记录

**第三步：记录DNS配置信息**
Vercel会显示类似这样的信息：
```
Type: CNAME
Name: www
Value: cname.vercel-dns.com

Type: A
Name: @
Value: 76.76.19.61
```

### 配置域名DNS记录

**在域名服务商管理界面**：

#### 方法一：使用域名服务商DNS

**以Namecheap为例**：
1. 登录Namecheap账号
2. 进入 "Domain List"
3. 点击域名旁的 "Manage" 按钮
4. 选择 "Advanced DNS" 标签

**添加DNS记录**：
```
Type: A Record
Host: @
Value: 76.76.19.61
TTL: Automatic

Type: CNAME Record
Host: www
Value: cname.vercel-dns.com
TTL: Automatic
```

#### 方法二：使用Cloudflare DNS（推荐）

**第一步：转移DNS到Cloudflare**
1. 注册Cloudflare账号：https://www.cloudflare.com
2. 添加你的域名
3. 记录Cloudflare提供的名称服务器：
   ```
   ns1.cloudflare.com
   ns2.cloudflare.com
   ```

**第二步：在域名注册商处修改DNS**
1. 回到Namecheap管理界面
2. 选择 "Domain" 标签
3. 修改 "Nameservers" 为Cloudflare提供的地址

**第三步：在Cloudflare添加DNS记录**
```
Type: A
Name: @
IPv4 address: 76.76.19.61
Proxy status: 🟠 Proxied

Type: CNAME
Name: www
Target: cname.vercel-dns.com
Proxy status: 🟠 Proxied
```

### 验证域名配置

**等待DNS生效**（5-30分钟）：
```bash
# 检查DNS解析
nslookup yourname.com

# 或者使用在线工具
# https://www.whatsmydns.net/
```

**Vercel验证**：
- 回到Vercel Domains设置
- 等待状态从 "Pending" 变为 "Valid"
- 点击域名测试访问

**🎉 成功标志**：通过自定义域名访问你的网站！

## 🔒 第三步：HTTPS和安全配置（5分钟）

### HTTPS自动配置

**Vercel自动化HTTPS**：
- SSL证书自动申请和安装
- 强制HTTPS重定向
- 证书自动续期

**验证HTTPS生效**：
1. 访问 `https://yourname.com`
2. 检查浏览器地址栏的锁形图标
3. 查看证书信息（点击锁形图标）

### 安全最佳实践

**在Vercel项目设置中启用**：

**Security Headers**：
```
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
```

**HSTS配置**：
```
Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
```

这些配置Vercel会自动处理，但了解它们的作用很重要。

## 📈 第四步：SEO基础优化（10分钟）

### Next.js内置SEO配置

**更新 `app/layout.tsx`**：
```tsx
import type { Metadata } from 'next'
import { Inter, Poppins } from 'next/font/google'
import './globals.css'
import Navigation from './components/Navigation'

const inter = Inter({
  subsets: ['latin'],
  variable: '--font-inter',
  display: 'swap'
})

const poppins = Poppins({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  variable: '--font-poppins',
  display: 'swap'
})

export const metadata: Metadata = {
  title: {
    default: '张伟 - UI/UX设计师 | 现代化前端开发',
    template: '%s | 张伟的作品集'
  },
  description: '张伟的个人作品集网站。UI/UX设计师，掌握现代化前端开发技术，包括React、Next.js、TypeScript和Tailwind CSS。展示设计作品和开发项目。',
  keywords: ['UI设计师', 'UX设计师', '前端开发', 'React', 'Next.js', 'TypeScript', 'Tailwind CSS', '作品集'],
  authors: [{ name: '张伟', url: 'https://yourname.com' }],
  creator: '张伟',
  publisher: '张伟',
  robots: {
    index: true,
    follow: true,
    googleBot: {
      index: true,
      follow: true,
      'max-video-preview': -1,
      'max-image-preview': 'large',
      'max-snippet': -1,
    },
  },
  openGraph: {
    type: 'website',
    locale: 'zh_CN',
    url: 'https://yourname.com',
    title: '张伟 - UI/UX设计师 | 现代化前端开发',
    description: '张伟的个人作品集网站。展示UI/UX设计作品和现代化前端开发项目。',
    siteName: '张伟的作品集',
    images: [
      {
        url: 'https://yourname.com/og-image.jpg',
        width: 1200,
        height: 630,
        alt: '张伟的作品集网站',
      },
    ],
  },
  twitter: {
    card: 'summary_large_image',
    title: '张伟 - UI/UX设计师 | 现代化前端开发',
    description: '张伟的个人作品集网站。展示UI/UX设计作品和现代化前端开发项目。',
    images: ['https://yourname.com/og-image.jpg'],
    creator: '@yourname',
  },
  verification: {
    google: 'your-google-verification-code',
    yandex: 'your-yandex-verification-code',
  },
  alternates: {
    canonical: 'https://yourname.com',
    languages: {
      'zh-CN': 'https://yourname.com',
      'en-US': 'https://yourname.com/en',
    },
  },
}

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="zh-CN" className={`${inter.variable} ${poppins.variable}`}>
      <body className={inter.className}>
        <Navigation />
        {children}
      </body>
    </html>
  )
}
```

### 创建Sitemap

**创建 `app/sitemap.ts`**：
```typescript
import { MetadataRoute } from 'next'

export default function sitemap(): MetadataRoute.Sitemap {
  const baseUrl = 'https://yourname.com'

  return [
    {
      url: baseUrl,
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 1,
    },
    {
      url: `${baseUrl}/about`,
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 0.8,
    },
    {
      url: `${baseUrl}/projects`,
      lastModified: new Date(),
      changeFrequency: 'weekly',
      priority: 0.9,
    },
    {
      url: `${baseUrl}/contact`,
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 0.7,
    },
  ]
}
```

### 创建Robots.txt

**创建 `app/robots.ts`**：
```typescript
import { MetadataRoute } from 'next'

export default function robots(): MetadataRoute.Robots {
  return {
    rules: {
      userAgent: '*',
      allow: '/',
      disallow: ['/api/', '/admin/'],
    },
    sitemap: 'https://yourname.com/sitemap.xml',
  }
}
```

### Google Search Console配置

**第一步：验证网站所有权**
1. 访问 [Google Search Console](https://search.google.com/search-console/)
2. 添加资源：`https://yourname.com`
3. 选择验证方法：HTML标签（推荐）

**第二步：添加验证代码**
复制Google提供的验证代码到 `app/layout.tsx` 的metadata中：
```tsx
verification: {
  google: 'your-verification-code-here',
},
```

**第三步：提交Sitemap**
在Google Search Console中：
1. 选择 "站点地图"
2. 添加新的站点地图：`https://yourname.com/sitemap.xml`
3. 点击提交

## 📊 第五步：性能和访问分析（5分钟）

### Google Analytics配置

**第一步：创建Google Analytics账号**
1. 访问 [Google Analytics](https://analytics.google.com/)
2. 创建新的GA4资源
3. 获取测量ID（格式：G-XXXXXXXXXX）

**第二步：安装Google Analytics**
```bash
npm install @next/third-parties
```

**第三步：配置Analytics**
在 `app/layout.tsx` 中添加：
```tsx
import { GoogleAnalytics } from '@next/third-parties/google'

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="zh-CN" className={`${inter.variable} ${poppins.variable}`}>
      <body className={inter.className}>
        <Navigation />
        {children}
        <GoogleAnalytics gaId="G-XXXXXXXXXX" />
      </body>
    </html>
  )
}
```

### 性能测试

**使用在线工具测试**：

1. **PageSpeed Insights**: https://pagespeed.web.dev/
   - 输入你的域名
   - 查看性能评分
   - 关注Core Web Vitals指标

2. **GTmetrix**: https://gtmetrix.com/
   - 全面的性能分析
   - 瀑布图分析
   - 优化建议

**目标性能指标**：
- Performance Score: >90
- Largest Contentful Paint (LCP): <2.5s
- Cumulative Layout Shift (CLS): <0.1
- First Input Delay (FID): <100ms

## 🤖 AI协作：域名和SEO优化

在Codex中尝试这些对话：

1. **域名选择建议**
   ```
   "作为UI设计师，如何选择一个好的个人品牌域名？"
   ```

2. **DNS配置问题**
   ```
   "DNS解析不生效，如何排查和解决问题？"
   ```

3. **SEO优化策略**
   ```
   "个人作品集网站的SEO优化重点是什么？"
   ```

4. **性能优化建议**
   ```
   "如何提升Next.js网站的Core Web Vitals评分？"
   ```

## 🎯 完成检查

- [ ] 成功购买并配置自定义域名
- [ ] 完成DNS解析和Vercel域名绑定
- [ ] HTTPS证书自动配置并生效
- [ ] 网站可通过自定义域名正常访问
- [ ] 配置完整的SEO meta信息
- [ ] 创建并提交sitemap.xml和robots.txt
- [ ] 验证Google Search Console所有权
- [ ] 安装Google Analytics追踪代码
- [ ] 通过性能测试并达到良好指标

## 🚀 恭喜你！

**你现在拥有一个真正专业的个人品牌网站！** 🎉

现在你的网站具备：
- 🌐 **专业域名**：yourname.com的品牌形象
- 🔒 **HTTPS安全**：绿锁标识的可信保障
- 📈 **SEO优化**：搜索引擎友好的结构
- 📊 **访问分析**：Google Analytics数据追踪
- ⚡ **高性能**：优秀的Core Web Vitals评分
- 💼 **职业优势**：可直接用于求职的专业网站

**你的网站地址现在就是你的个人品牌！**

从 `portfolio-v2-username.vercel.app` 到 `yourname.com`，这不仅是技术上的升级，更是专业形象的重大提升。

## 🎯 下一步

现在你已经拥有了专业的个人网站，是时候学习传统的部署方式，理解网站部署的底层原理了！

继续学习：[EP03: 云服务器部署](../EP03-server-deployment/) - 掌握传统服务器部署方式，理解网站运行的技术原理

---

**个人品牌的技术实现**：从一个普通的开发项目到专业的个人品牌网站，域名和优化配置起到了关键作用。现在你不仅有了技术作品，更有了专业形象！🎨→💻→🌐→🏆→✨