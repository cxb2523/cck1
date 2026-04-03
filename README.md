# 淘宝「我的淘宝 - 设置」页面个性化美化功能

本项目实现了淘宝「我的淘宝 - 设置」页面的个性化页面美化功能模块，完全符合淘宝现有页面设计风格。

## 功能特性

### 🎨 主题选择功能
- **官方主题资源接入**：通过模拟淘宝官方主题资源公共API接口获取最新主题数据
- **合规主题范围**：仅包含淘宝官方合规主题（经典橙、科技蓝、清新绿、浪漫紫）
- **实时预览**：支持主题切换的实时预览效果
- **一键切换**：点击即可切换主题，操作流畅

### 🌙 深浅模式联动
- **双模式支持**：支持浅色模式和深色模式
- **智能联动**：主题与模式联动选择，确保视觉一致性
- **舒适体验**：深色模式优化夜间使用体验

### 💾 配置持久化
- **本地存储**：使用localStorage保存用户主题配置
- **后端同步**：模拟向后端API发送配置数据
- **回显功能**：页面重新加载时自动恢复用户设置

## 项目结构

```
src/
├── components/
│   └── PersonalizationSettings.vue    # 个性化设置主组件
├── services/
│   └── themeApi.js                    # 淘宝主题API服务
├── App.vue                            # 主应用组件
├── main.js                            # 应用入口
└── style.css                          # 全局样式
```

## 技术栈

- **Vue 3** - 现代化前端框架
- **Vite** - 快速构建工具
- **CSS Variables** - 主题变量系统
- **LocalStorage** - 本地数据持久化

## 快速开始

### 安装依赖
```bash
npm install
```

### 启动开发服务器
```bash
npm run dev
```

### 构建生产版本
```bash
npm run build
```

## 核心功能实现

### 1. 主题API服务 (`src/services/themeApi.js`)

模拟淘宝官方主题资源API，提供：
- `getThemes()` - 获取官方主题列表
- `getUserThemeConfig()` - 获取用户主题配置
- `saveUserThemeConfig()` - 保存用户配置
- `validateThemeConfig()` - 验证配置有效性

### 2. 个性化设置组件 (`src/components/PersonalizationSettings.vue`)

主要功能模块：
- **主题选择网格**：可视化主题选择界面
- **模式切换**：深浅模式选择器
- **实时预览**：动态预览效果
- **配置保存**：一键应用设置

### 3. 主题变量系统 (`src/style.css`)

基于CSS变量的主题系统：
```css
:root {
  --primary-color: #ff5000;
  --primary-hover: #e44a00;
  /* ... 更多变量 */
}

[data-theme="blue"] {
  --primary-color: #1677ff;
  --primary-hover: #0958d9;
}

[data-theme-mode="dark"] {
  --text-primary: #ffffff;
  --bg-white: #1f1f1f;
  /* ... 暗色模式变量 */
}
```

## 主题配置数据格式

```json
{
  "theme": "default",
  "mode": "light",
  "userId": "demo_user_123",
  "lastModified": "2024-01-01T00:00:00Z"
}
```

## 淘宝设计规范遵循

1. **色彩系统**：使用淘宝官方品牌色系
2. **布局规范**：遵循淘宝移动端设计规范
3. **交互模式**：符合淘宝用户操作习惯
4. **视觉层次**：保持淘宝一贯的视觉风格

## 浏览器兼容性

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## 开发说明

### 添加新主题
1. 在 `themeApi.js` 的 `getThemes()` 方法中添加新主题数据
2. 在 `style.css` 中定义对应的CSS变量
3. 主题会自动出现在选择器中

### 自定义样式
项目使用CSS变量系统，可通过修改 `src/style.css` 中的变量值来自定义样式。

## 部署说明

项目构建后可直接部署到任何静态文件服务器，主题配置数据通过localStorage持久化，无需后端支持即可正常运行。

---

**注意**：本项目为演示用途，实际接入淘宝生产环境需要替换模拟API为真实的淘宝官方API接口。