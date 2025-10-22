---
layout: default
title: EP03：云服务器部署 - 传统部署方式掌握
permalink: /modules/04-professional-deployment/EP03-server-deployment/
---

# EP03: 云服务器部署 - 传统部署方式掌握 ⏱️ 55分钟

**🎧 EP03 配套播客**：
**🎵 云服务器部署：传统部署方式的完整掌握**

- [🎧 Internet Archive 收听](https://archive.org/details/04-ep-03-server-deployment) - 无需注册，直接播放
- [🎵 Spotify 收听](https://open.spotify.com/episode/04-ep-03-server-deployment) - 需要 Spotify 账号

---

## 🎯 这一步要完成什么

**理解网站部署的底层原理和传统方式**：

- 云服务商选择指导（国内：腾讯云、阿里云 vs 国外：AWS、Azure）☁️
- 服务器基础配置和安全设置（用户管理、防火墙、SSH）🔒
- Nginx安装配置和反向代理原理理解 🌐
- Let's Encrypt SSL证书配置和自动续期 🔐

**这55分钟将让你理解网站运行的技术原理，掌握传统部署的完整流程！** 🏗️

## 🤔 为什么要学习传统部署？（8分钟）

### Vercel vs 传统服务器的对比

**平台即服务(PaaS) vs 基础设施即服务(IaaS)**：

| 特性 | Vercel (PaaS) | 云服务器 (IaaS) |
|------|---------------|-----------------|
| 配置复杂度 | 零配置 | 需要手动配置 |
| 控制程度 | 有限 | 完全控制 |
| 成本 | 小项目免费 | 按需付费 |
| 学习价值 | 体验优化 | 原理理解 |
| 企业应用 | 适合快速原型 | 适合复杂系统 |

### 设计师理解传统部署的价值

**类比设计工作流**：
- **Vercel** = 使用Figma模板，快速出效果
- **服务器部署** = 从零开始设计，完全定制

**职业发展价值**：
- 理解网站运行的底层原理
- 具备与运维团队沟通的能力
- 掌握问题排查的基础技能
- 建立技术深度的认知基础

### 学习目标设定

**不是要成为运维专家**，而是：
- 理解网站如何在服务器上运行
- 掌握基础的服务器操作
- 建立网站部署的完整认知
- 具备简单问题的自主解决能力

## ☁️ 第一步：云服务商选择和注册（12分钟）

### 国内云服务商对比

#### 🇨🇳 腾讯云

**优势**：
- 新用户优惠力度大
- 文档中文化程度高
- 微信生态集成好
- 学生认证有额外优惠

**定价**（轻量应用服务器）：
- 1核1GB: ¥40/月
- 1核2GB: ¥60/月
- 2核2GB: ¥80/月

**适合场景**：
- 国内用户访问为主
- 需要微信小程序后端
- 预算有限的个人项目

**注册地址**：https://cloud.tencent.com/

#### 🇨🇳 阿里云

**优势**：
- 市场份额最大，生态完善
- 技术文档详细
- 企业级服务完善
- 国际节点多

**定价**（ECS突发性能实例）：
- 1核1GB: ¥45/月
- 1核2GB: ¥65/月
- 2核4GB: ¥130/月

**适合场景**：
- 企业级应用
- 需要完整云服务生态
- 对稳定性要求高

**注册地址**：https://www.aliyun.com/

### 国外云服务商对比

#### 🌍 AWS (Amazon Web Services)

**优势**：
- 全球最大云服务提供商
- 服务种类最全
- 国际化程度最高
- 免费层额度丰富

**定价**（EC2 t3.micro）：
- 1核1GB: $8-10/月
- 1核2GB: $16-20/月
- 免费层：t2.micro 750小时/月（12个月）

**适合场景**：
- 国际化应用
- 需要全球部署
- 学习云服务技术栈

**注册地址**：https://aws.amazon.com/

#### 🌍 Microsoft Azure

**优势**：
- 微软生态集成
- 企业级服务强
- 混合云解决方案好
- 开发者工具集成

**定价**（B1s虚拟机）：
- 1核1GB: $7-9/月
- 1核2GB: $14-18/月
- 免费层：$200信用额度（30天）

**适合场景**：
- .NET应用开发
- 企业级Windows应用
- 需要微软生态集成

**注册地址**：https://azure.microsoft.com/

### 推荐选择策略

**个人学习项目推荐**：
1. **首选**：腾讯云轻量应用服务器（价格便宜，中文服务）
2. **备选**：AWS EC2（免费层，国际化）

**实际演示选择**：腾讯云轻量应用服务器

### 腾讯云服务器购买演示

**第一步：注册和实名认证**
1. 访问 https://cloud.tencent.com/
2. 使用手机号注册账号
3. 完成实名认证（个人认证即可）

**第二步：选择轻量应用服务器**
1. 进入控制台
2. 选择 "轻量应用服务器"
3. 点击 "新建"

**第三步：服务器配置**
```
地域: 广州（选择离你最近的）
镜像: Ubuntu 22.04 LTS
实例套餐: 1核1GB 40GB SSD（¥40/月）
购买时长: 1个月（学习足够）
```

**第四步：网络和安全**
```
带宽: 3Mbps（基础套餐包含）
安全组: 默认（开放22, 80, 443端口）
```

**第五步：完成购买**
- 确认配置和价格
- 选择支付方式
- 完成购买

**🎉 成功标志**：服务器状态显示"运行中"！

## 🖥️ 第二步：服务器基础配置（15分钟）

### 连接服务器

**获取连接信息**：
在腾讯云控制台中：
1. 找到你的服务器实例
2. 记录公网IP地址
3. 设置或重置密码

**连接方式选择**：

#### 方法一：使用腾讯云控制台（推荐初学者）
1. 在服务器列表中点击 "登录"
2. 选择 "VNC登录"
3. 输入用户名 `ubuntu` 和密码

#### 方法二：使用SSH客户端

**Windows用户**：
```powershell
# 使用PowerShell
ssh ubuntu@your-server-ip
```

**macOS/Linux用户**：
```bash
# 使用终端
ssh ubuntu@your-server-ip
```

**首次连接**：
```bash
# 输入密码后，更新系统
sudo apt update && sudo apt upgrade -y
```

### 创建普通用户

**为什么不用root用户**：
- 安全风险高
- 误操作危险大
- 最佳实践推荐

**创建新用户**：
```bash
# 创建用户（替换为你的名字）
sudo adduser yourname

# 添加sudo权限
sudo usermod -aG sudo yourname

# 切换到新用户
su - yourname
```

### 配置SSH密钥（安全性提升）

**生成SSH密钥对**（在本地电脑执行）：
```bash
# 生成密钥对
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"

# 查看公钥内容
cat ~/.ssh/id_rsa.pub
```

**在服务器上配置公钥**：
```bash
# 创建.ssh目录
mkdir -p ~/.ssh

# 编辑authorized_keys文件
nano ~/.ssh/authorized_keys

# 粘贴你的公钥内容，保存退出

# 设置正确权限
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

**测试密钥登录**：
```bash
# 从本地连接（无需密码）
ssh yourname@your-server-ip
```

### 配置防火墙

**Ubuntu防火墙配置**：
```bash
# 启用UFW防火墙
sudo ufw enable

# 允许SSH连接
sudo ufw allow ssh

# 允许HTTP
sudo ufw allow 80

# 允许HTTPS
sudo ufw allow 443

# 查看防火墙状态
sudo ufw status
```

**防火墙规则解释**：
- 22端口：SSH远程连接
- 80端口：HTTP网站访问
- 443端口：HTTPS安全访问

## 🌐 第三步：安装和配置Nginx（12分钟）

### 理解Nginx的作用

**什么是Nginx**：
- Web服务器软件
- 反向代理服务器
- 负载均衡器

**Nginx在部署中的角色**：
```
用户请求 → Nginx → Next.js应用 → 返回页面
```

**设计师理解**：
- Nginx = 网站的门卫
- 负责接收访问请求
- 转发给正确的应用程序

### 安装Nginx

```bash
# 更新包列表
sudo apt update

# 安装Nginx
sudo apt install nginx -y

# 启动Nginx服务
sudo systemctl start nginx

# 设置开机自启
sudo systemctl enable nginx

# 检查Nginx状态
sudo systemctl status nginx
```

**验证Nginx安装**：
- 在浏览器访问你的服务器IP地址
- 应该看到 "Welcome to nginx!" 页面

### Nginx基础配置

**理解Nginx配置结构**：
```
/etc/nginx/
├── nginx.conf              # 主配置文件
├── sites-available/         # 可用站点配置
├── sites-enabled/          # 启用站点配置
└── conf.d/                 # 额外配置目录
```

**创建网站配置**：
```bash
# 创建配置文件
sudo nano /etc/nginx/sites-available/portfolio
```

**基础配置内容**：
```nginx
server {
    listen 80;
    server_name your-domain.com www.your-domain.com your-server-ip;

    root /var/www/portfolio;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    # 安全头设置
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header X-Content-Type-Options "nosniff" always;

    # Gzip压缩
    gzip on;
    gzip_vary on;
    gzip_min_length 1024;
    gzip_types text/plain text/css text/xml text/javascript application/javascript application/xml+rss application/json;
}
```

**启用站点配置**：
```bash
# 创建符号链接
sudo ln -s /etc/nginx/sites-available/portfolio /etc/nginx/sites-enabled/

# 删除默认配置
sudo rm /etc/nginx/sites-enabled/default

# 测试配置
sudo nginx -t

# 重新加载Nginx
sudo systemctl reload nginx
```

### 部署静态网站

**创建网站目录**：
```bash
# 创建网站根目录
sudo mkdir -p /var/www/portfolio

# 修改目录权限
sudo chown -R $USER:$USER /var/www/portfolio
sudo chmod -R 755 /var/www/portfolio
```

**创建测试页面**：
```bash
# 创建测试页面
nano /var/www/portfolio/index.html
```

**测试页面内容**：
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio - 服务器部署成功</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            max-width: 800px;
            margin: 2rem auto;
            padding: 2rem;
            line-height: 1.6;
            color: #333;
        }
        .success {
            background: #d4edda;
            border: 1px solid #c3e6cb;
            color: #155724;
            padding: 1rem;
            border-radius: 0.375rem;
            margin: 1rem 0;
        }
        .info {
            background: #cce7ff;
            border: 1px solid #99d6ff;
            color: #0066cc;
            padding: 1rem;
            border-radius: 0.375rem;
            margin: 1rem 0;
        }
    </style>
</head>
<body>
    <h1>🎉 服务器部署成功！</h1>

    <div class="success">
        <strong>恭喜！</strong> 你的Portfolio网站已成功部署到云服务器上。
    </div>

    <h2>部署信息</h2>
    <ul>
        <li><strong>服务器</strong>: Ubuntu 22.04 LTS</li>
        <li><strong>Web服务器</strong>: Nginx</li>
        <li><strong>部署时间</strong>: <script>document.write(new Date().toLocaleString('zh-CN'))</script></li>
        <li><strong>IP地址</strong>: <?php echo $_SERVER['SERVER_ADDR'] ?? 'Unknown'; ?></li>
    </ul>

    <div class="info">
        <strong>下一步</strong>: 配置SSL证书，启用HTTPS安全访问
    </div>

    <h2>技术栈</h2>
    <p>这个页面演示了传统的Web服务器部署方式：</p>
    <ul>
        <li>云服务器提供计算资源</li>
        <li>Nginx处理HTTP请求</li>
        <li>静态文件直接服务</li>
        <li>未来可扩展为动态应用</li>
    </ul>
</body>
</html>
```

**验证部署**：
访问你的服务器IP地址，应该看到测试页面！

## 🔐 第四步：SSL证书配置（8分钟）

### 理解SSL证书的重要性

**HTTP vs HTTPS**：
- HTTP: 明文传输，不安全
- HTTPS: 加密传输，安全可靠

**Let's Encrypt优势**：
- 免费SSL证书
- 自动化申请和续期
- 被所有主流浏览器信任

### 安装Certbot

```bash
# 安装snapd（如果未安装）
sudo apt install snapd -y

# 安装certbot
sudo snap install --classic certbot

# 创建certbot命令链接
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

### 申请SSL证书

**自动配置Nginx**：
```bash
# 使用certbot自动配置
sudo certbot --nginx -d your-domain.com -d www.your-domain.com
```

**交互式配置过程**：
1. 输入邮箱地址（用于证书到期通知）
2. 同意服务条款（输入A）
3. 选择是否共享邮箱（输入N）
4. 选择重定向选项（推荐选择2：重定向所有HTTP到HTTPS）

**手动申请证书（如果自动配置失败）**：
```bash
# 仅申请证书，不自动配置
sudo certbot certonly --nginx -d your-domain.com -d www.your-domain.com
```

### 更新Nginx配置（手动申请时需要）

如果手动申请证书，需要更新Nginx配置：

```bash
# 编辑站点配置
sudo nano /etc/nginx/sites-available/portfolio
```

**HTTPS配置**：
```nginx
# HTTP重定向到HTTPS
server {
    listen 80;
    server_name your-domain.com www.your-domain.com;
    return 301 https://$server_name$request_uri;
}

# HTTPS配置
server {
    listen 443 ssl http2;
    server_name your-domain.com www.your-domain.com;

    # SSL证书配置
    ssl_certificate /etc/letsencrypt/live/your-domain.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/your-domain.com/privkey.pem;

    # SSL安全配置
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers off;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384;

    # 网站内容配置
    root /var/www/portfolio;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    # 安全头设置
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header X-Content-Type-Options "nosniff" always;
}
```

**重新加载Nginx**：
```bash
# 测试配置
sudo nginx -t

# 重新加载
sudo systemctl reload nginx
```

### 配置自动续期

**测试自动续期**：
```bash
# 测试续期命令
sudo certbot renew --dry-run
```

**查看续期任务**：
```bash
# 查看cron任务
sudo crontab -l
```

Let's Encrypt证书默认90天有效期，certbot会自动配置续期任务。

**验证HTTPS**：
访问 `https://your-domain.com`，应该看到：
- 浏览器地址栏显示锁形图标
- 证书信息显示Let's Encrypt颁发
- HTTP自动重定向到HTTPS

## 🚀 第五步：优化和监控（5分钟）

### 基础性能优化

**启用Gzip压缩**（已在Nginx配置中包含）：
```nginx
gzip on;
gzip_vary on;
gzip_min_length 1024;
gzip_types text/plain text/css text/xml text/javascript application/javascript application/xml+rss application/json;
```

**缓存设置**：
```nginx
# 在server块中添加
location ~* \.(jpg|jpeg|png|gif|ico|css|js)$ {
    expires 1y;
    add_header Cache-Control "public, immutable";
}
```

### 基础监控

**服务器资源监控**：
```bash
# 查看CPU和内存使用
htop

# 查看磁盘使用
df -h

# 查看网络连接
netstat -tulpn
```

**Nginx访问日志**：
```bash
# 查看访问日志
sudo tail -f /var/log/nginx/access.log

# 查看错误日志
sudo tail -f /var/log/nginx/error.log
```

**服务状态监控**：
```bash
# 检查Nginx状态
sudo systemctl status nginx

# 检查防火墙状态
sudo ufw status

# 检查SSL证书状态
sudo certbot certificates
```

### 基础安全配置

**定期更新系统**：
```bash
# 创建更新脚本
nano ~/update_system.sh
```

**更新脚本内容**：
```bash
#!/bin/bash
echo "开始系统更新..."
sudo apt update
sudo apt upgrade -y
sudo apt autoremove -y
echo "系统更新完成！"
```

**设置定期更新**：
```bash
# 添加执行权限
chmod +x ~/update_system.sh

# 添加到cron任务（每周日凌晨2点执行）
(crontab -l ; echo "0 2 * * 0 /home/yourname/update_system.sh") | crontab -
```

## 🤖 AI协作：服务器管理和问题排查

在Codex中尝试这些对话：

1. **服务器配置优化**
   ```
   "Ubuntu服务器部署Next.js应用的最佳实践配置？"
   ```

2. **Nginx配置问题**
   ```
   "Nginx配置SSL后出现502错误，如何排查和解决？"
   ```

3. **性能优化建议**
   ```
   "小型个人网站在云服务器上的性能优化策略？"
   ```

4. **安全配置加强**
   ```
   "个人云服务器需要配置哪些基础安全设置？"
   ```

## 🎯 完成检查

- [ ] 成功购买并配置云服务器
- [ ] 完成服务器基础安全配置
- [ ] 安装并配置Nginx Web服务器
- [ ] 部署测试网站并验证访问
- [ ] 配置Let's Encrypt SSL证书
- [ ] 启用HTTPS并设置HTTP重定向
- [ ] 配置基础性能优化设置
- [ ] 设置SSL证书自动续期
- [ ] 理解服务器监控和维护方法

## 🚀 恭喜你！

**你已经掌握了传统服务器部署的完整流程！** 🎉

现在你理解了：
- 🖥️ **服务器管理**：云服务器的购买、配置和维护
- 🌐 **Web服务器**：Nginx的安装、配置和优化
- 🔐 **SSL证书**：HTTPS的配置和自动续期
- 🛡️ **安全配置**：防火墙、用户权限和安全头设置
- 📊 **基础监控**：日志查看和系统状态监控

**技术深度的重要价值**：

虽然Vercel部署更简单，但掌握传统部署让你：
- 理解网站运行的底层原理
- 具备问题排查的基础能力
- 在面试中展现技术深度
- 为复杂项目部署做好准备

**对比两种部署方式**：
- **Vercel**: 适合快速原型和小型项目
- **云服务器**: 适合生产环境和复杂需求

## 🎯 下一步

现在你已经掌握了两种部署方式，是时候学习如何监控和优化网站性能，建立可持续的运营能力了！

继续学习：[EP04: 监控维护和通用优化](../EP04-monitoring-optimization/) - 建立完整的网站监控和优化体系

---

**传统部署的价值**：虽然现代化平台让部署变得简单，但理解底层原理让你成为更专业的开发者。现在你不仅会使用工具，更理解工具背后的技术实现！🎨→💻→🖥️→🔧→✨