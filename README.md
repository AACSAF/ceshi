# 简易网站 - Cloudflare Pages 部署

这是一个使用HTML、CSS和JavaScript构建的现代化响应式网站，部署在Cloudflare Pages上。

## 功能特点

- 🎨 现代化的UI设计
- 📱 完全响应式，适配所有设备
- ⚡ 优化的性能和加载速度
- 🎭 流畅的动画效果
- 🔒 安全的头部配置
- ☁️ 部署在Cloudflare Pages上

## 项目结构

```
├── index.html          # 主页面
├── styles.css          # 样式文件
├── script.js           # JavaScript功能
├── package.json        # 项目配置
├── _headers           # Cloudflare Pages 头部配置
├── _redirects         # 重定向配置
└── README.md          # 项目说明
```

## 本地开发

1. 克隆项目到本地
2. 在项目目录中运行以下命令启动本地服务器：

```bash
# 使用Python（推荐）
python -m http.server 8000

# 或使用Node.js
npx serve .

# 或使用PHP
php -S localhost:8000
```

3. 在浏览器中访问 `http://localhost:8000`

## 部署到Cloudflare Pages

### 方法一：通过Git仓库部署（推荐）

1. 将代码推送到GitHub、GitLab或Bitbucket
2. 登录Cloudflare Dashboard
3. 进入Pages部分
4. 点击"创建项目"
5. 连接你的Git仓库
6. 配置构建设置：
   - 构建命令：`npm run build`（可选）
   - 构建输出目录：`/`（根目录）
7. 点击"保存并部署"

### 方法二：直接上传文件

1. 登录Cloudflare Dashboard
2. 进入Pages部分
3. 点击"上传资源"
4. 将所有文件拖拽到上传区域
5. 点击"部署站点"

## 自定义域名

1. 在Cloudflare Pages项目中点击"自定义域"
2. 添加你的域名
3. 按照提示配置DNS记录

## 环境变量（如果需要）

在Cloudflare Pages项目设置中可以添加环境变量：
- 生产环境变量
- 预览环境变量

## 性能优化

- 启用了Cloudflare的CDN加速
- 配置了适当的缓存头部
- 优化了图片和资源加载
- 使用了现代CSS和JavaScript特性

## 浏览器支持

- Chrome (最新版本)
- Firefox (最新版本)
- Safari (最新版本)
- Edge (最新版本)

## 许可证

MIT License

## 联系方式

如有问题或建议，请通过网站联系表单或邮件联系。
