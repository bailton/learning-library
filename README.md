
## 更新后的 README.md

```markdown
# 📚 Learning Library

> 个人知识管理工具 · 分类书架 + 多级编号 + 阅读模式 · 跨设备同步

---

## 🎯 项目定位

这是一个**个人知识管理工具**，按主题（分类）整理你学到的知识碎片，像"数字书架"一样管理学习笔记。

---

## 🧩 功能清单

| 功能 | 说明 |
|------|------|
| 📂 分类管理 | 自定义分类（书架），支持新建/编辑/删除 |
| 📝 快速添加 | 首页顶部快速添加记录，支持分类/标题/内容/来源 |
| 📖 按标题排列 | 支持多级编号排序（1, 1.1, 1.1.1, 2, 2.1...） |
| 📋 按日期排列 | 支持正序/倒序切换 |
| 📖 阅读模式 | 沉浸式阅读界面，左侧目录侧边栏（可收起），键盘翻页 |
| ✏️ 编辑记录 | 编辑标题、内容、来源、排序编号 |
| ☁️ 云端存储 | 数据通过 **GitHub Gist API** 保存到 Private Gist |
| 📱 跨设备同步 | 手机、电脑、平板共用同一份数据 |
| 📤 导出/导入备份 | JSON 格式数据备份和恢复 |
| 🗑️ 清空所有 | 一键重置所有数据（同步到 Gist） |

---

## 📝 内容格式支持

| 效果 | 输入方式 | 示例 |
|------|----------|------|
| **加粗** | `**文字**` | `**重要**` → **重要** |
| *斜体* | `*文字*` | `*注意*` → *注意* |
| 列表 | `- 项目` | `- 苹果` → • 苹果 |
| 链接 | `[文字](网址)` | `[Google](https://google.com)` |
| 换行 | `Enter` | 换行但不分段 |
| 空行（分段） | 两次 `Enter` | 段落间留空 |

---

## 🏗️ 技术架构

| 层级 | 技术 | 说明 |
|------|------|------|
| **前端** | Vue 2.7 (CDN) | 轻量级响应式框架，单 HTML 文件 |
| **托管** | Cloudflare Pages | 静态网站托管 |
| **存储** | **GitHub Private Gist** | 通过 Gist API 存储数据 |
| **存储格式** | `{ categories: [...], records: [...] }` | 分类 + 记录分开存储 |
| **本地缓存** | localStorage | 离线缓存和快速加载兜底 |

---

## 📦 数据格式

### 分类（Category）

```json
{
  "id": "health",
  "name": "Health",
  "icon": "🏥",
  "_editing": false
}
```

### 记录（Record）

```json
{
  "id": "rec_1234567890",
  "categoryId": "health",
  "title": "维生素D与免疫力",
  "content": "第一段\n\n第二段\n**加粗文字**",
  "source": "哈佛健康杂志",
  "order": "1.1",
  "createdAt": "2026-07-07T10:30:00.000Z",
  "updatedAt": "2026-07-07T10:30:00.000Z"
}
```

---

## 🔑 环境配置

| 配置项 | 说明 | 获取方式 |
|--------|------|----------|
| **Gist ID** | GitHub Gist 的唯一标识 | 创建 Gist 后，从 URL 复制 |
| **GitHub Token** | 访问 Gist API 的凭证 | Settings → Developer settings → Personal access tokens → 勾选 `gist` 权限 |

### 配置步骤

1. 登录 GitHub，创建 **Private Gist**，文件名为 `learning-library.json`，内容为 `{"categories":[],"records":[]}`
2. 从浏览器地址栏复制 **Gist ID**
3. 生成 **Personal Access Token**（勾选 `gist` 权限）
4. 在网页顶部填入 Gist ID 和 Token
5. 点击 **"连接并同步"**

---

## 📁 文件结构

```
learning-library/
├── index.html          # 完整应用（单页 HTML）
└── README.md           # 项目说明文档（本文件）
```

---

## 🔄 版本历史

### v1.2.0 (2026-07-07)

**新增**
- 阅读模式（沉浸式阅读界面）
- 左侧目录侧边栏（可收起）
- 阅读模式键盘翻页（← →）
- 首次打开阅读模式默认显示目录页

**修复**
- 内容换行保留（`\n` → `<br>`）
- 加粗 `**文字**` 和斜体 `*文字*` 正确渲染
- 列表 `- 项目` 正确渲染
- 多级编号排序逻辑修复（1 → 1.1 → 1.1.1）

### v1.1.0 (2026-07-06)

**新增**
- 分类管理弹窗（编辑/删除分类）
- 默认"未分类"分类
- 日期排序正序/倒序切换
- 标题排序正序/倒序切换
- 多级编号支持（1, 1.1, 1.1.1）

### v1.0.0 (2026-07-06)

- 首次发布
- 分类管理（书架）
- 快速添加记录
- 按日期/标题排列
- GitHub Gist 同步

---

## 🚀 部署方式

### 当前部署

- **平台**: Cloudflare Pages
- **方式**: Direct Upload
- **访问地址**: `https://learning-library.pages.dev`

### 更新步骤

1. 修改 `index.html` 代码
2. 登录 Cloudflare Pages → 进入 `learning-library` 项目
3. Deployments → New deployment → Direct Upload
4. 拖入 `index.html` → 点击 Deploy
5. 等待 10-20 秒，刷新页面

---

## 🧠 设计决策记录

| 决策 | 原因 |
|------|------|
| **单 HTML 文件** | 部署简单，无需构建工具 |
| **Vue 2 CDN** | 轻量、无需 npm install |
| **GitHub Gist 存储** | 免费、无 CORS 限制、数据归用户所有 |
| **Private Gist** | 数据仅自己可见，安全可控 |
| **Markdown 风格语法** | 纯文本存储，跨设备一致，无需富文本编辑器 |

---

## 📎 相关链接

| 链接 | 说明 |
|------|------|
| [GitHub Gist](https://gist.github.com) | 数据存储平台 |
| [Cloudflare Pages](https://pages.cloudflare.com) | 网站托管平台 |
| [Vue.js](https://vuejs.org) | 前端框架 |

---

## 🤖 AI 助手阅读指南

如果你是一个 AI 助手，需要理解这个项目：

1. **这是一个单 HTML 应用**，所有代码在 `index.html` 中
2. **核心数据**：`categories`（分类列表）和 `records`（记录列表）
3. **核心方法**：
   - `renderContent()`: 将 Markdown 风格文本转为 HTML（加粗、斜体、列表、换行）
   - `saveToGist()`: 通过 Gist API 上传数据
   - `loadFromGist()`: 从 Gist API 拉取数据
   - `openReader()`: 打开阅读模式
4. **存储格式**：Gist 中存的是 `{ categories: [...], records: [...] }`
5. **认证方式**：使用 `Authorization: token <GitHub Token>` 请求头
6. **部署方式**：Cloudflare Pages Direct Upload

---

*最后更新: 2026-07-07*
```
