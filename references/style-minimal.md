# Style C — 极简留白（Minimal）

参考感觉：图1（Google Fonts蓝灰）、图6（Solowire白底）、图7（灰底打字机诗意）

## 核心气质
克制、安静、文字即设计。大量留白不是"空"，而是"呼吸"。字体选择和间距就是全部的设计语言。图7那种手写/打字机质感适合诗意内容，图6那种无衬线适合专业/技术内容。

## 配色方案

### 方案一：暖灰纸质（图7感觉）
- 背景：`#e8e4de` 或 `#ddd8d0`（温暖灰，像旧纸）
- 文字：`#2a2420`（近黑，略暖）
- 辅助文字：`#8a8078`
- 无任何强调色，靠层级和间距说话

### 方案二：冷白专业（图6感觉）
- 背景：`#ffffff` 或 `#f7f7f5`
- 主文字：`#111111`
- 强调：极少量，只用字重区分，或一处细节用黑色粗体
- 辅助：`#999`

### 方案三：蓝灰沉静（图1感觉）
- 背景：`#5a6a7a` 或 `#4a5a6a`（蓝灰）
- 文字：`#ffffff`（主）/ `rgba(255,255,255,0.7)`（副）
- 完全不用装饰，靠背景颜色营造气氛

## 字体
```html
<!-- 打字机/诗意风（图7） -->
<link href="https://fonts.googleapis.com/css2?family=Courier+Prime:ital@0;1&family=Noto+Serif+SC:wght@300;400&display=swap" rel="stylesheet">

<!-- 专业极简风（图6） -->
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500&family=Noto+Sans+SC:wght@300;400;500&display=swap" rel="stylesheet">

<!-- 沉静蓝灰风（图1） -->
<link href="https://fonts.googleapis.com/css2?family=Lora:ital@0;1&family=Noto+Serif+SC:wght@300;400&display=swap" rel="stylesheet">
```

根据内容选：诗/情绪类 → 打字机；技术/干货 → 专业极简；沉思/观点 → 沉静蓝灰。

## 排版核心原则

### 留白比例
- 上下边距：**至少 140px**，不手软
- 左右边距：**100-120px**
- 文字区域不超过卡片面积的 **50%**
- 行距：**2.0-2.2**（比其他风格更大）

### 字号（克制）
```
主标题：60-80px（不要贪大）
副标题/引导语：36-40px，字重 300
正文：28-32px，字重 300，行距 2.0
注释/日期：22px，右对齐或居中
```

### 图7打字机排版特征
- 文字**右对齐**（不常见，很有个性）
- 或者居中，但字间距极大（`letter-spacing: 0.15em`）
- 底部放2-3个小图（用CSS色块模拟老照片边框感）：
```css
.photo-placeholder {
  width: 120px;
  height: 90px;
  background: #2a2420;
  border: 3px solid #2a2420;
  display: inline-block;
  margin-right: 16px;
  /* 模拟老照片 */
  filter: sepia(0.3) contrast(1.1);
}
```

### 图6引用块格式
```html
<div style="border-left: 3px solid #111; padding-left: 40px; margin: 80px 0;">
  <div style="font-size: 80px; font-weight: 300; line-height: 1.1; color: #111;">❝</div>
  <p style="font-size: 36px; font-weight: 400; line-height: 1.8;">引用内容</p>
  <p style="font-size: 26px; color: #666; margin-top: 20px;">— 来源</p>
</div>
```

## 封面页结构
极简封面：**不要装饰**，只有文字。
```
[大量留白，上方约 280px 空白]
[主标题，左对齐或居中，不超过3行]
[一条细线，宽 80px，左对齐]
[副标题，字重300，行距2.0]
[大量留白]
[底部极小：日期 或 账号名，右对齐]
```

## 结尾页
延续克制风格，不用感叹号，用句号。互动引导可以写成一句话而非标签组。
例：「如果这些字刚好有用，欢迎收藏。」
