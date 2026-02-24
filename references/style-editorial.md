# Style B — 编辑杂志（Editorial）

参考感觉：图3（Roboto Serif杂志排版）、图4（紫色插画书页）

## 核心气质
有强烈的印刷出版物质感。文字密度高但层级清晰，字号对比强烈，可以有单色插图/几何图形，像一本精心设计的书或杂志内页。

## 配色方案

### 方案一：黑白印刷
- 背景：`#f8f6f1`（略微泛黄的纸白）
- 主文字：`#0f0f0f`
- 强调色：任选一个单色（紫 `#7b68ee`、红 `#e84040`、绿 `#2d6a4f`）
- 辅助：`#888`（注释/页码）

### 方案二：单色主题（如图4的紫）
- 背景：`#fafafa`
- 强调色块/插图：单一颜色填充，如 `#8b7fdc`
- 其余全部黑白

## 字体
```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=Noto+Serif+SC:wght@300;400;700&family=Space+Mono:ital@0;1&display=swap" rel="stylesheet">
```

- **超大展示标题**：`Playfair Display` 900，可以非常大（160-200px），允许溢出裁切
- **中文标题**：`Noto Serif SC` 700
- **正文**：`Noto Serif SC` 300，小字（28-32px），行距1.9
- **注释/标签/页码**：`Space Mono`，全小写或全大写，极小字号

## 排版规则

### 字号层级（严格执行）
```
超大展示：160-200px（可裁切，做视觉冲击）
大标题：80-100px
小标题/章节：40-48px，加粗或全大写+字间距
正文：28-34px
注释/页码：22-26px，Space Mono
```

### 多栏布局（内容页可用）
```css
.two-col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  padding: 0 80px;
}
```

### 首字下沉（长文章封面内容页）
```css
.drop-cap::first-letter {
  font-size: 120px;
  font-weight: 900;
  float: left;
  line-height: 0.85;
  margin-right: 16px;
  margin-top: 8px;
  color: #7b68ee; /* 用强调色 */
}
```

### 文字溢出装饰（封面）
大标题故意让文字超出卡片边缘，`overflow: hidden` 裁切，制造张力感：
```css
.oversized-title {
  font-size: 220px;
  white-space: nowrap;
  overflow: hidden;
  width: 100%;
}
```

## 装饰元素
- 粗细不一的横线（`border-top: 8px solid` / `border-top: 1px solid`）
- 圆形/方形单色色块作为"插图占位"
- 页码格式：`2 / 11`，右下角，Space Mono

## 封面页结构
```
[窄顶条：期刊名/账号名，极小字]
[粗分隔线 8px]
[超大标题，可允许右侧裁切]
[正文摘要，左侧两栏或单栏]
[细分隔线]
[底部：作者/日期 + 页码]
```

## 结尾页
保持印刷感，用大引号 `"` 或 `❝` 开头写一句有分量的话，下面是互动引导，风格偏理性克制。
