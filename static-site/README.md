# 网页工具箱 - 静态网站

一个功能完善的个人网页工具管理系统，可直接部署在 GitHub Pages 上。

## 功能特性

### 核心功能
- **工具管理**：上传、编辑、删除个人网页工具
- **访问控制**：所有者密码保护的管理功能
- **工具分享**：一键生成可分享链接
- **访客使用**：无需登录即可使用工具
- **分类浏览**：支持分类筛选和搜索

### 新增功能
- ✅ **所有者名称**：首次设置时可设置所有者名称，可随时修改
- ✅ **URL导入**：支持通过网页链接导入工具
- ✅ **美化上传界面**：重新设计的上传表单，包含图标选择器
- ✅ **数据备份**：支持导出/导入数据备份文件，跨设备同步

### 技术特点
- 100% 纯前端实现，无需后端服务器
- 数据存储在浏览器的 IndexedDB 中
- 响应式设计，适配各种设备
- 零依赖部署，可直接部署到 GitHub Pages

## 快速开始

### 本地预览

1. 下载或克隆此仓库
2. 直接在浏览器中打开 `index.html`
3. 或使用本地服务器：

```bash
# Python 3
python -m http.server 8000

# Node.js (npx)
npx serve .

# PHP
php -S localhost:8000
```

然后访问 http://localhost:8000

### 首次设置

1. 首次打开网站，点击"登录"进入认证页面
2. 系统会提示您设置所有者名称和密码（至少6位）
3. 设置完成后即可使用完整的管理功能

## GitHub Pages 部署指南

### 方法一：使用 GitHub 网页界面（推荐新手）

#### 步骤 1：创建新仓库

1. 登录 GitHub 账号
2. 点击右上角的 **+** → **New repository**
3. 填写仓库名称（如 `my-web-tools`）
4. 选择 **Public**（公开仓库才能使用 GitHub Pages）
5. 点击 **Create repository**

#### 步骤 2：上传文件

1. 在仓库页面点击 **uploading an existing file**
2. 将 `static-site` 文件夹内的所有文件拖拽到上传区域
3. 确保包含以下文件：
   - `index.html`
   - `login.html`
   - `dashboard.html`
   - `tool.html`
   - `css/style.css`
   - `js/app.js`
4. 点击 **Commit changes**

#### 步骤 3：启用 GitHub Pages

1. 进入仓库的 **Settings**（设置）页面
2. 滚动到 **Pages** 左侧菜单
3. 在 **Source** 部分：
   - Branch: 选择 `main`
   - Folder: 选择 `/ (root)`
   - 点击 **Save**
4. 等待 1-2 分钟，页面会显示您的网站地址

#### 步骤 4：访问网站

网站地址格式：`https://yourusername.github.io/repository-name/`

例如：`https://username.github.io/my-web-tools/`

---

### 方法二：使用 Git 命令行

#### 步骤 1：在 GitHub 创建仓库

1. 登录 GitHub，点击 **+** → **New repository**
2. 填写仓库名称，**不要**初始化 README
3. 点击 **Create repository**
4. 复制仓库的 HTTPS 或 SSH 地址

#### 步骤 2：本地初始化

```bash
# 进入 static-site 文件夹
cd static-site

# 初始化 Git 仓库
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit"

# 添加远程仓库（替换为您的仓库地址）
git remote add origin https://github.com/yourusername/your-repo.git

# 推送到 GitHub
git push -u origin main
```

#### 步骤 3：启用 GitHub Pages

1. 进入 GitHub 仓库的 **Settings**
2. 左侧菜单点击 **Pages**
3. Source 选择 `main` 分支和 `/ (root)` 文件夹
4. 点击 **Save**

---

## 使用说明

### 访客使用

1. 打开网站首页
2. 浏览所有可用的网页工具
3. 使用搜索和分类筛选
4. 点击"使用"按钮打开工具
5. 点击"分享"复制工具链接

### 所有者功能

1. **登录**：点击"登录"按钮，输入密码
2. **上传工具**：
   - 点击"上传工具"按钮
   - 选择"上传文件"或"导入链接"
   - 填写工具名称、描述、选择分类和图标
   - 点击"保存"
3. **编辑工具**：点击工具卡片上的"编辑"按钮
4. **删除工具**：点击"删除"按钮确认删除
5. **修改设置**：点击"设置"按钮修改网站名称、描述和所有者名称
6. **备份数据**：在设置页面点击"导出备份"下载数据文件
7. **恢复数据**：在设置页面点击"导入备份"选择备份文件

### 文件要求

上传的工具文件需满足以下条件：

- **必须包含**：至少一个 HTML 文件（上传文件方式）
- **支持格式**：
  - HTML: `.html`, `.htm`
  - 样式: `.css`
  - 脚本: `.js`
  - 数据: `.json`
  - 图片: `.png`, `.jpg`, `.jpeg`, `.gif`, `.svg`, `.ico`
- **大小限制**：单个文件建议不超过 5MB
- **编码**：文件需使用 UTF-8 编码

### URL导入

通过链接方式导入工具：

1. 输入完整的网页URL（如 `https://example.com/tool.html`）
2. 填写工具信息
3. 系统会直接嵌入该网页

⚠️ **注意**：由于 CORS 限制，部分网站可能无法正常加载。

### 数据存储

所有数据存储在浏览器的 IndexedDB 中：

- **工具数据**：IndexedDB
- **登录状态**：SessionStorage

⚠️ **重要**：更换设备时，请先在设置页面导出备份文件，然后在新设备上导入恢复数据。

---

## 自定义域名（可选）

1. 购买域名（阿里云、腾讯云等）
2. 在域名服务商添加 DNS 记录：
   - 类型：A
   - 值：`185.199.108.153`（GitHub Pages IP）
3. 在 GitHub 仓库 Settings → Pages → Custom domain 输入您的域名
4. 启用 HTTPS

---

## 注意事项

### 局限性

1. **数据限制**：由于使用本地存储，建议工具数量不超过 50 个
2. **文件大小**：大文件可能占用过多存储空间
3. **隐私**：数据存储在用户本地，服务端无法访问

### 安全建议

1. **定期备份**：定期导出重要工具数据
2. **密码保护**：设置强密码保护管理功能
3. **HTTPS**：GitHub Pages 自动提供 HTTPS

### 浏览器兼容

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

---

## 文件结构

```
static-site/
├── index.html          # 首页（工具展示）
├── login.html          # 登录页面
├── dashboard.html      # 管理面板
├── tool.html           # 工具详情页
├── css/
│   └── style.css       # 样式文件
├── js/
│   └── app.js          # 核心功能脚本
├── assets/             # 资源文件夹（可放置图片等）
├── tools/              # 工具文件夹（示例工具）
│   └── calculator.html # 示例：计算器工具
└── README.md           # 详细部署指南
```

---

## 更新日志

### v1.1.0 (2024)
- 新增所有者名称设置功能
- 新增 URL 导入工具功能
- 美化上传界面，添加图标选择器
- 添加数据备份与恢复功能
- 使用 IndexedDB 替代 LocalStorage
- 修复已知问题

### v1.0.0 (2024)
- 初始版本发布
- 支持工具上传、编辑、删除
- 支持分享功能
- 响应式设计
- GitHub Pages 部署支持

---

## 许可证

MIT License
