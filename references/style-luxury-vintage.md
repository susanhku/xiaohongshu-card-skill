# Style A — 奢华复古（Luxury Vintage）

参考感觉：图2（粉底金字拱形）、图5（奶油黄vintage排版）

## 核心气质
高端、精致、复古欧式。字体本身就是主视觉，装饰符号点缀，留白克制但不空洞。

## 配色方案

### 方案一：粉金
- 背景：`#fdf0e8` 或 `#f9e8df`（温柔裸粉）
- 主文字：`#b8860b` / `#c9973a`（哑金）
- 副文字：`#8b6348`（深驼色）
- 装饰线：`#d4a96a`（浅金）
- 强调块：`rgba(212,169,106,0.15)`

### 方案二：奶油黑
- 背景：`#f5f0e0`（奶油黄）
- 主文字：`#1a1208`（近黑）
- 强调色：`#c9973a`（金）
- 副文字：`#5c4a2a`

## 字体（Google Fonts）
```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,600;1,300;1,600&family=Noto+Serif+SC:wght@300;400;700&family=Cinzel:wght@400;700&display=swap" rel="stylesheet">
```

- **大标题**：`Cormorant Garamond` 600，极大字号（120-160px），可用斜体
- **英文装饰标签**：`Cinzel` 400，字间距 `0.3em`，全大写
- **中文正文**：`Noto Serif SC` 300/400
- **数字页码**：`Cormorant Garamond` italic

## 装饰元素（纯CSS/SVG/字符，不用图片）
```
符号库：✦ ✧ ✺ ❋ ◆ — ⌒  ✿  ❧
拱形：用 border-radius: 50% 50% 0 0 做半圆顶装饰块
细线：1px solid，opacity 0.4
菱形分隔：◆ 左右各一条细线
```

### 拱形装饰（封面常用）
```css
.arch {
  width: 200px;
  height: 280px;
  border: 1.5px solid #d4a96a;
  border-radius: 100px 100px 0 0;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 40px;
}
```

### 分隔线组合
```html
<div style="display:flex;align-items:center;gap:20px;margin:40px 0;">
  <div style="flex:1;height:1px;background:#d4a96a;opacity:0.6;"></div>
  <span style="color:#d4a96a;font-size:24px;">✦</span>
  <div style="flex:1;height:1px;background:#d4a96a;opacity:0.6;"></div>
</div>
```

## 封面页结构
```
[大量上方留白]
[拱形SVG装饰 或 品牌符号]
[LA ——— CA 类标签行]
[超大衬线主标题，2-3行]
[副标题，全大写，字间距大]
[✦ 小符号]
[下方留白]
[右下角页码：italic 01/0N]
```

## 内容页结构
```
[顶部：英文小标签 CHAPTER 01 或 — NOTE —]
[大标题，左对齐或居中]
[细分隔线]
[正文：Noto Serif SC 300，行距1.8，不要太密]
[底部页码]
```

## 结尾页
背景加深（驼色或深粉），白色/金色文字，保持奢华感。引导语用优雅措辞，避免"点赞收藏"这种直白说法，改成"若有共鸣，愿与你相遇 ✦"之类。
