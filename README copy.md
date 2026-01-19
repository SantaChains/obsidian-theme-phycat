# Phycat Obsidian 主题

## 主题介绍
Phycat 是一款为 Obsidian 笔记应用设计的自定义主题，旨在提供美观、舒适的用户体验。

## 安装方法

1. **手动安装**：
   - 下载本主题文件夹
   - 将其复制到你的 Obsidian 库的 `.obsidian/themes/` 目录中
   - 打开 Obsidian 设置 → 外观 → 主题，选择 "Phycat"

2. **从 Obsidian 社区安装**：
   - 打开 Obsidian 设置 → 外观 → 主题
   - 点击 "浏览" 按钮
   - 在社区主题列表中搜索 "Phycat"
   - 点击 "安装并使用"

## 开发环境设置

### 前提条件
- Git 已安装
- 代码编辑器（推荐 Visual Studio Code）

### 步骤
1. **克隆主题仓库**：
   ```bash
   cd path/to/vault/.obsidian/themes
   git clone <repository-url> "Phycat"
   ```

2. **启用主题**：
   - 打开 Obsidian 设置 → 外观 → 主题
   - 从下拉列表中选择 "Phycat"

3. **更新 manifest.json**：
   - 修改主题名称、描述等信息
   - 注意：每次修改 manifest.json 后需要重启 Obsidian

## CSS 变量系统

Obsidian 使用 CSS 变量来设置用户界面的样式。以下是一些常用的 CSS 变量：

### 基础变量
- `--font-text-theme`：文本字体
- `--font-ui-theme`：UI 字体
- `--font-monospace-theme`：等宽字体

### 颜色变量

#### 浅色主题
```css
.theme-light {
  --background-primary: #ffffff;
  --background-secondary: #f7f6f3;
  --text-normal: #37352f;
  --text-muted: #6b7280;
  --text-accent: #2563eb;
  --interactive-normal: #e5e7eb;
  --interactive-hover: #d1d5db;
  --interactive-accent: #2563eb;
}
```

#### 深色主题
```css
.theme-dark {
  --background-primary: #191919;
  --background-secondary: #232323;
  --text-normal: #e6e6e6;
  --text-muted: #9ca3af;
  --text-accent: #60a5fa;
  --interactive-normal: #374151;
  --interactive-hover: #4b5563;
  --interactive-accent: #60a5fa;
}
```

### 布局变量
- `--ribbon-background`：侧边栏背景
- `--sidebar-background`：侧边栏背景
- `--canvas-background`：画布背景

## 调试方法

### 使用 Chrome DevTools
1. **打开开发者工具**：
   - Windows/Linux: Ctrl+Shift+I
   - macOS: Cmd+Option+I

2. **查看 CSS 变量**：
   - 打开 "Sources" 选项卡
   - 选择 "Page → top → obsidian.md → app.css"
   - 滚动到顶部查看所有可用的 CSS 变量

3. **检查元素**：
   - 点击左上角的选择器图标
   - 点击 Obsidian 界面中的元素
   - 在 "Styles" 选项卡中查看应用的 CSS

### 设置断点
```typescript
function yourFunction() {
  // 在此处放置你的代码
  debugger; // 作为断点
}
```

### 性能分析
1. **打开开发者工具** → "Performance" 选项卡
2. **点击 Record 按钮** 或按 Ctrl+E
3. **执行你的操作**
4. **停止记录** 并查看火焰图

## 开发指南

### 1. 更改字体
```css
body {
  --font-text-theme: Georgia, serif;
  --font-ui-theme: system-ui, sans-serif;
  --font-monospace-theme: 'Fira Code', monospace;
}
```

### 2. 更改颜色
```css
.theme-light {
  --background-primary: #f8f9fa;
  --background-secondary: #e9ecef;
}

.theme-dark {
  --background-primary: #1a1a1a;
  --background-secondary: #2d2d2d;
}
```

### 3. 更改输入框样式
```css
:root {
  --input-focus-border-color: Highlight;
  --input-focus-outline: 1px solid Canvas;
  --input-unfocused-border-color: transparent;
  --input-disabled-border-color: transparent;
  --input-hover-border-color: #cbd5e0;
}
```

### 4. 响应式设计
```css
@media screen and (max-width: 768px) {
  body {
    --font-text-theme: system-ui, sans-serif;
    font-size: 14px;
  }
}
```

## 最佳实践

1. **使用语义化的 CSS 类名**
2. **保持 CSS 结构清晰**
3. **使用 CSS 变量而非硬编码值**
4. **同时支持浅色和深色主题**
5. **测试不同屏幕尺寸**
6. **定期更新主题以兼容 Obsidian 新版本**

## 常见问题

### Q: 主题不生效怎么办？
A: 尝试以下步骤：
1. 重启 Obsidian
2. 检查主题文件夹名称是否与 manifest.json 中的 name 属性匹配
3. 确保 theme.css 文件存在且包含有效 CSS

### Q: 如何找到特定元素的 CSS 变量？
A: 使用 Chrome DevTools 的元素选择器，点击目标元素，在 "Styles" 选项卡中查看应用的 CSS 变量。

### Q: 如何添加自定义字体？
A: 在 theme.css 中添加 @font-face 规则，然后通过 CSS 变量应用：
```css
@font-face {
  font-family: 'CustomFont';
  src: url('fonts/custom-font.woff2') format('woff2');
}

body {
  --font-text-theme: 'CustomFont', sans-serif;
}
```

## 贡献

欢迎提交 Issue 和 Pull Request 来改进这个主题！

## 许可证

本主题采用 MIT 许可证。

---

**注意**：本主题仅用于美化 Obsidian 界面，不会修改任何功能或数据。

*最后更新：2026-01-19*