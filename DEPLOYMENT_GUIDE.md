# Cloudflare Pages 部署完整指南

本指南将详细介绍如何将你的简易网站部署到Cloudflare Pages。

## 前提条件

1. 一个Cloudflare账户（免费即可）
2. 网站文件已准备就绪
3. （可选）Git仓库用于自动部署

## 部署方法

### 方法一：Git仓库自动部署（推荐）

#### 步骤1：准备Git仓库

1. 在GitHub、GitLab或Bitbucket上创建新仓库
2. 将网站文件推送到仓库：

```bash
git init
git add .
git commit -m "初始提交：简易网站"
git branch -M main
git remote add origin https://github.com/yourusername/your-repo.git
git push -u origin main
```

#### 步骤2：连接Cloudflare Pages

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 在左侧菜单中选择 "Pages"
3. 点击 "创建项目" 或 "Connect to Git"
4. 选择你的Git提供商（GitHub/GitLab/Bitbucket）
5. 授权Cloudflare访问你的仓库
6. 选择要部署的仓库

#### 步骤3：配置构建设置

```
项目名称: your-website-name
生产分支: main
构建命令: npm run build （可留空）
构建输出目录: / （根目录）
环境变量: （暂时留空）
```

#### 步骤4：部署

1. 点击 "保存并部署"
2. 等待构建完成（通常1-3分钟）
3. 部署成功后会获得一个 `.pages.dev` 域名

### 方法二：直接文件上传

#### 步骤1：准备文件

确保以下文件在同一个文件夹中：
- index.html
- styles.css
- script.js
- _headers
- _redirects
- package.json

#### 步骤2：上传到Cloudflare Pages

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 选择 "Pages" → "上传资源"
3. 输入项目名称
4. 将所有文件拖拽到上传区域
5. 点击 "部署站点"

## 自定义域名设置

### 步骤1：添加自定义域名

1. 在Pages项目中点击 "自定义域"
2. 点击 "设置自定义域"
3. 输入你的域名（例如：www.yoursite.com）

### 步骤2：配置DNS

如果域名在Cloudflare管理：
- DNS记录会自动添加

如果域名在其他服务商：
- 添加CNAME记录：`www` → `your-project.pages.dev`
- 或添加A记录指向Cloudflare IP

### 步骤3：SSL证书

- Cloudflare会自动为你的域名提供免费SSL证书
- 通常在几分钟内生效

## 高级配置

### 环境变量

在项目设置中可以添加环境变量：

```
生产环境:
SITE_NAME=我的网站
CONTACT_EMAIL=contact@yoursite.com

预览环境:
SITE_NAME=我的网站（测试）
CONTACT_EMAIL=test@yoursite.com
```

### 构建钩子

设置Webhook用于自动部署：
1. 进入项目设置
2. 找到 "构建钩子"
3. 创建新的钩子
4. 复制URL用于外部触发部署

### 访问策略

配置访问限制：
1. 进入项目设置
2. 选择 "访问策略"
3. 可设置密码保护或IP白名单

## 性能优化建议

### 1. 启用Cloudflare功能

- **Auto Minify**: 自动压缩CSS、JS、HTML
- **Brotli压缩**: 更好的压缩率
- **Rocket Loader**: 异步加载JavaScript

### 2. 缓存配置

在 `_headers` 文件中已配置：
```
/styles.css
  Cache-Control: public, max-age=31536000

/script.js
  Cache-Control: public, max-age=31536000
```

### 3. 图片优化

- 使用WebP格式
- 启用Cloudflare的图片优化
- 考虑使用Cloudflare Images

## 监控和分析

### 1. Cloudflare Analytics

- 访问量统计
- 性能指标
- 安全事件

### 2. Web Vitals

- 页面加载速度
- 用户体验指标
- 性能建议

### 3. 实时日志

- 访问日志
- 错误日志
- 安全日志

## 故障排除

### 常见问题

1. **部署失败**
   - 检查文件结构
   - 确认构建命令正确
   - 查看构建日志

2. **404错误**
   - 检查 `_redirects` 文件
   - 确认文件路径正确
   - 验证DNS设置

3. **SSL证书问题**
   - 等待证书生成（最多24小时）
   - 检查DNS配置
   - 联系Cloudflare支持

### 调试步骤

1. 检查构建日志
2. 验证文件上传完整性
3. 测试本地版本
4. 检查浏览器控制台错误

## 成本说明

### Cloudflare Pages 免费套餐包含：

- 无限静态请求
- 每月500次构建
- 100GB带宽
- 自定义域名
- 免费SSL证书

### 付费功能：

- 更多构建次数
- 高级分析
- 优先支持

## 下一步

部署成功后，你可以：

1. 设置自定义域名
2. 配置CDN和缓存
3. 添加分析工具
4. 设置监控告警
5. 优化SEO设置

## 支持资源

- [Cloudflare Pages 文档](https://developers.cloudflare.com/pages/)
- [Cloudflare 社区](https://community.cloudflare.com/)
- [GitHub Issues](https://github.com/cloudflare/pages-action/issues)

---

**恭喜！** 你的网站现在已经部署在全球CDN上，享受快速、安全、可靠的服务。
