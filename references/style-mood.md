# Style D/E — 图文氛围（Mood Board）

参考感觉：图8（胶片复古ins帖子）、图9（珍珠牡蛎自然光产品）

> 这两种风格结构相同，差异在于滤镜和色调。用户上传图片时使用。
> 没有图片时，用CSS渐变色块模拟，并在代码注释里告诉用户替换方式。

---

## Mood-Bright — 明亮自然光（图9感觉）

### 核心气质
通透、干净、自然光打亮。像在阳光下拍摄，奶油白底，文字轻盈，有高端生活方式感。

### 配色
- 背景：`#f5f0e8`（温暖米白）
- 图片区：占卡片上方约55-60%
- 文字区背景：`#faf7f2` 或 纯白
- 主文字：`#2c2016`
- 辅助文字：`#8a7a6a`
- 强调：`#c9973a`（金棕）或 `#7a9e7e`（自然绿）

### 图片处理（CSS滤镜）
```css
.card-image {
  width: 100%;
  height: 780px; /* 约54%卡片高度 */
  object-fit: cover;
  object-position: center;
  filter: brightness(1.05) saturate(0.9) contrast(1.02);
  /* 明亮自然光：略提亮，略降饱和，保持通透 */
}
```

### 无图时的占位
```css
.image-placeholder {
  width: 100%;
  height: 780px;
  background: linear-gradient(135deg, #e8ddd0 0%, #d4c4b0 50%, #c8b89a 100%);
  /* 在代码注释中写：将此div替换为 <img src="你的图片" class="card-image"> */
}
```

### 字体
```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant:ital,wght@0,300;0,500;1,300&family=Noto+Serif+SC:wght@300;400&family=DM+Sans:wght@300;400&display=swap" rel="stylesheet">
```
- 标题：`Cormorant` 或 `Noto Serif SC` 300（轻盈）
- 正文：`DM Sans` 300 或 `Noto Serif SC` 300
- 标签：`DM Sans` 400，全大写，字间距大

### 布局结构
```
[图片区，占上方 55%，圆角 16px]
[文字区]
  [产品名/标题，大]
  [分类标签，小，全大写]
  [正文，两栏或单栏，字号小，Noto Serif 300]
  [底部：小红点导航点 或 页码]
```

### 图9参考细节
- 文字分成2-3列，每列有独立的小标题+列表
- 圆角卡片感（整张卡片 `border-radius: 20px`）
- 顶部有3个小圆点（导航指示）

---

## Mood-Film — 复古胶片（图8感觉）

### 核心气质
颗粒感、偏冷绿或偏黄的胶片色调、暗部压深、像从胶卷里扫描出来的照片。文字像帖子注释，克制而有情绪。

### 配色
- 整体底色：`#3d4a3e`（深墨绿）或 `#2a3028`（更暗）
- 图片区：占上方 50-55%，圆角
- 文字区背景：同底色或略浅 `#4a5a4a`
- 主文字：`#e8e0d0`（暖米白）
- 辅助文字：`rgba(232,224,208,0.6)`
- 强调：`#a0c4a0`（胶片绿）或 `#d4b896`（胶片黄）

### 图片处理（胶片滤镜）
```css
.card-image {
  width: 100%;
  height: 720px;
  object-fit: cover;
  border-radius: 16px;
  filter: 
    sepia(0.25)           /* 轻微泛黄 */
    saturate(0.75)        /* 降饱和 */
    contrast(1.1)         /* 提对比 */
    brightness(0.88);     /* 压暗 */
}

/* 叠加颗粒感（伪元素） */
.image-wrap::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 16px;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.08'/%3E%3C/svg%3E");
  opacity: 0.5;
  pointer-events: none;
  mix-blend-mode: overlay;
}
```

### 字体
```html
<link href="https://fonts.googleapis.com/css2?family=Courier+Prime:ital@0;1&family=Noto+Serif+SC:wght@300;400&display=swap" rel="stylesheet">
```
- 所有文字：`Courier Prime`（英文）+ `Noto Serif SC` 300（中文）
- 像图8：用等宽字体营造"帖子文字"感

### 布局结构（模拟图8的ins帖子感）
```
[图片区，圆角，上方略有内边距]
[操作栏：♥ 表情图标  ···  🔖，用CSS模拟]
[点赞数，小字]
[正文，分段，像帖子正文一样自然]
[时间戳 + 翻译按钮，极小，辅助色]
```

### 图8参考细节
- 整个卡片有一个深色背景（不是白色）
- 图片有圆角并且和卡片边缘有间距（`padding: 20px`）
- 文字区域在图片下方，像真实的ins帖子
- 互动图标用emoji或Unicode符号模拟：`♡` `⊙` `···` `🔖`

---

## 共同注意事项

1. **用户没有图片时**：在代码注释写清楚替换方式，用渐变色块占位，颜色要符合对应风格的色调
2. **图片路径**：使用相对路径或让用户粘贴本地路径，不要用外部URL
3. **多张卡片时**：第1张封面可以图片占主导，内容页图片比例降低，文字增多
