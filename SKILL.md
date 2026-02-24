---
name: xiaohongshu-card
description: 生成小红书风格多张竖版卡片（3:4比例，1080×1440px），输出单个HTML文件，支持逐张下载JPG或一键打包ZIP。当用户提到"小红书卡片"、"小红书图文"、"生成卡片"、"做成卡片"、"笔记卡片"、"种草卡片"、"知识卡片"、"分享卡片"、"整理成图文"、"做成图片"等时必须使用此skill。用户带图片且想做成卡片时也要用。
---

# 小红书卡片生成 Skill

## 第一步：判断风格

根据用户的描述或关键词，选择对应风格，然后**读取对应的 reference 文件**获取详细规范。

| 用户说的关键词 | 风格 | 读取文件 |
|-------------|------|---------|
| 复古、高级感、奢华、vintage、金色、精致 | A — 奢华复古 | `references/style-luxury-vintage.md` |
| 杂志、editorial、排版、印刷感、多栏 | B — 编辑杂志 | `references/style-editorial.md` |
| 留白、极简、克制、简约、文字感、诗意 | C — 极简留白 | `references/style-minimal.md` |
| 带图片 + 明亮、自然光、ins、通透 | D — 图文明亮 | `references/style-mood.md`（读 Mood-Bright 节） |
| 带图片 + 胶片、复古、暗调、氛围感 | E — 图文胶片 | `references/style-mood.md`（读 Mood-Film 节） |

**用户没有指定风格时**：根据内容主题自动判断——
- 美妆/好物/生活方式 → A
- 干货/知识/教程 → B 或 C
- 情绪/文字/诗 → C
- 用户上传了图片 → D 或 E（问用户明亮还是胶片）

---

## 第二步：规划卡片结构

读完风格文件后，规划卡片数量和内容分布：

- **封面页**（必须）：大标题 + 副标题/一句话概括
- **内容页**（1-6张）：每张聚焦一个要点，不要硬塞信息
- **结尾页**（必须）：互动引导 + 可选署名

内容页数量原则：宁少勿多，每张信息量不超过卡片70%高度。

---

## 第三步：写 HTML

读取 `references/layout-templates.md` 获取通用代码结构，结合风格文件的配色和字体规范来实现。

### 关键技术规范

**卡片尺寸**
```css
.card {
  width: 1080px;
  height: 1440px;
  overflow: hidden;
  position: relative;
}
```

**页面缩放显示**（不影响导出）
```css
.card {
  transform: scale(0.38);
  transform-origin: top center;
  margin-bottom: -893px; /* 1440 * (1-0.38) = 892.8 */
}
```

**JPG 导出**（html2canvas + JSZip + FileSaver）
```javascript
// 导出前临时还原真实尺寸
async function downloadCard(cardId, filename) {
  const card = document.getElementById(cardId);
  card.style.transform = 'scale(1)';
  card.style.marginBottom = '0';
  await document.fonts.ready;
  const canvas = await html2canvas(card, {
    width: 1080, height: 1440, scale: 2,
    useCORS: true, logging: false
  });
  card.style.transform = '';
  card.style.marginBottom = '';
  canvas.toBlob(b => saveAs(b, filename), 'image/jpeg', 0.95);
}

// 批量打包
async function downloadAll() {
  const zip = new JSZip();
  const cards = document.querySelectorAll('.card');
  for (let i = 0; i < cards.length; i++) {
    const card = cards[i];
    card.style.transform = 'scale(1)';
    card.style.marginBottom = '0';
    await document.fonts.ready;
    const canvas = await html2canvas(card, { width:1080, height:1440, scale:2, useCORS:true });
    card.style.transform = '';
    card.style.marginBottom = '';
    const blob = await new Promise(r => canvas.toBlob(r, 'image/jpeg', 0.95));
    zip.file(`card-${String(i+1).padStart(2,'0')}.jpg`, blob);
  }
  const content = await zip.generateAsync({ type: 'blob' });
  saveAs(content, '小红书卡片.zip');
}
```

**CDN 引用**（固定用这几个）
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.5/FileSaver.min.js"></script>
```

### 注意事项
- 不使用外部图片URL（跨域），装饰用CSS渐变、SVG、emoji代替
- 用户带图片时，引导用户自行替换 `src`，或在代码注释中说明
- 每张卡片内容不能溢出，绝不出现滚动条
- 控制栏（下载按钮）在卡片外部，不参与导出

---

## 第四步：输出

- 文件保存到 `/mnt/user-data/outputs/小红书卡片_[主题].html`
- 用 `present_files` 分享给用户
- 告知用户：浏览器打开即可预览和下载
