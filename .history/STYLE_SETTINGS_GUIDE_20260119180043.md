# Obsidian Style Settings 插件使用指南

## 插件介绍

Style Settings 是一款为 Obsidian 设计的强大插件，它允许主题、代码片段和插件通过 CSS 文件定义一组可配置的设置选项，使用户能够在一个统一的设置面板中调整所有可定制的选项。

### 主要功能

- **CSS 变量调整**：允许用户调整数值、字符串和颜色类型的 CSS 变量
- **类切换**：可以在 body 元素上切换类的开启和关闭
- **统一设置面板**：将所有可调整的设置集中在一个面板中，方便用户管理
- **支持多种设置类型**：包括标题、信息文本、类切换、类选择、文本变量、数字变量、滑块、下拉选择和颜色选择等

## 安装方法

1. **从 Obsidian 社区插件库安装**：
   - 打开 Obsidian 设置 → 社区插件 → 浏览
   - 搜索 "Style Settings"
   - 点击 "安装" 按钮
   - 安装完成后，启用插件

2. **手动安装**：
   - 从 GitHub 下载插件的最新发布版本
   - 将下载的文件解压到你的 Obsidian 库的 `.obsidian/plugins/` 目录中
   - 重启 Obsidian
   - 在设置中启用插件

## 基本使用方法

### 1. 在 CSS 文件中定义设置

Style Settings 通过 CSS 文件中的特殊注释来定义可配置的设置。这些注释以 `/* @settings` 开头，包含 YAML 格式的设置定义。

#### 基本结构

```css
/* @settings

name: 你的设置区域名称
id: 唯一标识符
settings:
    - 
        id: 设置项ID
        title: 设置项标题
        description: 设置项描述（可选）
        type: 设置类型
        # 其他设置属性

*/
```

### 2. 查看和调整设置

安装并启用插件后，你可以在 Obsidian 设置中找到 "Style Settings" 选项。点击它会打开一个面板，显示所有已定义的可调整设置。

## 设置类型详解

### 1. 标题 (heading)

用于组织和分组设置，创建可折叠的嵌套部分。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: section-title
        title: 基本设置
        type: heading
        level: 2
        collapsed: false

*/
```

### 2. 信息文本 (info-text)

向用户显示任意信息文本，支持 Markdown 格式。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: info-section
        title: 使用说明
        description: "这是一个 *Markdown* 格式的说明文本"
        type: info-text
        markdown: true

*/
```

### 3. 类切换 (class-toggle)

在 body 元素上切换 CSS 类的开启和关闭。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: dark-mode
        title: 深色模式
        description: 启用深色模式
        type: class-toggle
        default: false

*/
```

### 4. 类选择 (class-select)

创建一个预定义选项的下拉菜单，用于选择要添加到 body 元素的类。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: theme-variant
        title: 主题变体
        description: 选择主题的不同变体
        type: class-select
        allowEmpty: false
        default: light
        options:
            - 
                label: 浅色主题
                value: light
            - 
                label: 深色主题
                value: dark
            - 
                label: 高对比度
                value: high-contrast

*/
```

### 5. 文本变量 (variable-text)

用于设置基于文本的 CSS 变量。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: font-family
        title: 字体
        description: 界面使用的字体
        type: variable-text
        default: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif

*/
```

### 6. 数字变量 (variable-number)

用于设置数值类型的 CSS 变量。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: font-size
        title: 字体大小
        description: 基础字体大小（像素）
        type: variable-number
        default: 16
        format: px

*/
```

### 7. 滑块变量 (variable-number-slider)

使用滑块来设置数值类型的 CSS 变量。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: line-width
        title: 行宽
        description: 最大行宽（rem）
        type: variable-number-slider
        default: 42
        min: 20
        max: 60
        step: 1
        format: rem

*/
```

### 8. 选择变量 (variable-select)

创建一个预定义选项的下拉菜单，用于设置文本类型的 CSS 变量。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: font-style
        title: 字体样式
        description: 选择字体样式
        type: variable-select
        default: normal
        options:
            - normal
            - italic
            - oblique

*/
```

### 9. 颜色变量 (variable-color)

创建一个颜色选择器，用于设置颜色类型的 CSS 变量。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: accent-color
        title: 强调色
        description: 界面强调色
        type: variable-color
        format: hex
        opacity: false
        default: '#007AFF'

*/
```

### 10. 主题颜色变量 (variable-themed-color)

创建两个颜色选择器，分别用于浅色和深色主题。

```css
/* @settings

name: 示例设置
id: example-settings
settings:
    - 
        id: accent-color
        title: 强调色
        description: 界面强调色
        type: variable-themed-color
        format: hex
        opacity: false
        default-light: '#007AFF'
        default-dark: '#2DB253'

*/
```

## 在主题中集成 Style Settings

### 1. 主题配置示例

下面是一个完整的主题配置示例，包含了各种类型的设置：

```css
/* @settings

name: Phycat 主题设置
id: phycat-theme-settings
settings:
    - 
        id: general-section
        title: 基本设置
        type: heading
        level: 2
    - 
        id: font-family
        title: 字体
        description: 界面使用的字体
        type: variable-text
        default: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif
    - 
        id: font-size
        title: 字体大小
        description: 基础字体大小（像素）
        type: variable-number-slider
        default: 16
        min: 12
        max: 24
        step: 1
        format: px
    - 
        id: colors-section
        title: 颜色设置
        type: heading
        level: 2
    - 
        id: accent-color
        title: 强调色
        description: 界面强调色
        type: variable-themed-color
        format: hex
        opacity: false
        default-light: '#007AFF'
        default-dark: '#2DB253'
    - 
        id: background-color
        title: 背景色
        description: 界面背景色
        type: variable-themed-color
        format: hex
        opacity: false
        default-light: '#ffffff'
        default-dark: '#191919'
    - 
        id: text-color
        title: 文本颜色
        description: 界面文本颜色
        type: variable-themed-color
        format: hex
        opacity: false
        default-light: '#37352f'
        default-dark: '#e6e6e6'
    - 
        id: features-section
        title: 功能设置
        type: heading
        level: 2
    - 
        id: enable-custom-scrollbar
        title: 自定义滚动条
        description: 启用自定义滚动条样式
        type: class-toggle
        default: true
    - 
        id: enable-reading-mode-focus
        title: 阅读模式焦点
        description: 在阅读模式中启用文本焦点效果
        type: class-toggle
        default: false

*/
```

### 2. 主题 CSS 中使用设置的变量

在主题的 CSS 文件中，你可以使用通过 Style Settings 定义的变量：

```css
/* 导入设置变量 */
:root {
  /* 这里会自动填充通过 Style Settings 定义的变量 */
}

/* 使用变量 */
body {
  font-family: var(--font-family);
  font-size: var(--font-size);
  color: var(--text-color);
  background-color: var(--background-color);
}

/* 使用类切换 */
body.enable-custom-scrollbar ::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}

body.enable-custom-scrollbar ::-webkit-scrollbar-track {
  background: var(--background-secondary);
}

body.enable-custom-scrollbar ::-webkit-scrollbar-thumb {
  background: var(--interactive-normal);
  border-radius: 4px;
}

body.enable-custom-scrollbar ::-webkit-scrollbar-thumb:hover {
  background: var(--interactive-hover);
}
```

## 高级技巧

### 1. 颜色格式选项

`variable-color` 类型支持多种颜色格式：

- `hex`：十六进制格式（#007AFF）
- `rgb`：RGB 格式（rgb(0, 122, 255)）
- `rgb-values`：RGB 值格式（0, 122, 255）
- `rgb-split`：分离的 RGB 值（--accent-r: 0; --accent-g: 122; --accent-b: 255）
- `hsl`：HSL 格式（hsl(211, 100%, 50%)）
- `hsl-values`：HSL 值格式（211, 100%, 50%）
- `hsl-split`：分离的 HSL 值（--