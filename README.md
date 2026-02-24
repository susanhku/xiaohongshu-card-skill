# 🎴 小红书卡片生成 Skill

一个让 Claude 生成高质量小红书竖版卡片的 Skill，支持多种设计风格，输出 HTML 文件，可逐张或批量导出 JPG。

---

## 效果预览

| 奢华复古 | 编辑杂志 | 极简留白 | 图文氛围 |
|---------|---------|---------|---------|
| 粉金配色、拱形装饰、衬线大字 | 多栏排版、印刷质感、强字号对比 | 大量留白、打字机/专业两种子风格 | 带图片，明亮或胶片滤镜 |

---

## 支持的风格

| 关键词 | 风格 | 适合内容 |
|--------|------|---------|
| 复古、高级感、奢华、金色、vintage | **A — 奢华复古** | 美妆、好物、生活方式 |
| 杂志、排版、editorial、印刷感 | **B — 编辑杂志** | 深度内容、多段落干货 |
| 留白、极简、克制、诗意、简约 | **C — 极简留白** | 文字内容、情绪表达、金句 |
| 带图 + 明亮、自然光、ins、通透 | **D — 图文明亮** | 产品种草、旅行打卡 |
| 带图 + 胶片、复古、氛围感、暗调 | **E — 图文胶片** | 生活记录、情绪帖子 |

---

## 安装方法

### 方法一：Claude.ai 网页 / App

1. 下载 `xiaohongshu-card.skill`（或 `.zip`）文件
2. 打开 Claude.ai → **Settings** → **Capabilities**
3. 找到 **Skills** 区域，点击 **Upload skill**
4. 上传文件即可

### 方法二：Claude Code（命令行）

```bash
# 下载并解压到全局 skills 目录
unzip xiaohongshu-card.skill -d ~/.claude/skills/

# 验证安装
ls ~/.claude/skills/xiaohongshu-card/
# 应该看到：SKILL.md  references/
```

> 也可以放到项目级：`.claude/skills/xiaohongshu-card/`，只对当前项目生效。

### 方法三：GitHub 直接 Clone

```bash
git clone https://github.com/你的用户名/xiaohongshu-card-skill.git ~/.claude/skills/xiaohongshu-card
```

---

## 使用方法

安装后，直接在对话里描述你想要的卡片，Claude 会自动识别并使用这个 Skill：

```
帮我做一套小红书卡片，主题是"早起的5个好习惯"，奢华复古风格

把这篇文章整理成小红书图文卡片，极简留白风

我有一张照片，帮我做成胶片感的小红书卡片，配上文字

生成一套关于"断舍离"的知识卡片，杂志排版风格
```

### 输出说明

- 输出为单个 `.html` 文件
- 在浏览器中打开即可预览所有卡片
- 每张卡片下方有**单独下载**按钮（JPG）
- 顶部有**一键打包下载**按钮（ZIP，含所有 JPG）
- 卡片尺寸：**1080 × 1440px**，3:4 比例，适合直接发小红书

---

## 文件结构

```
xiaohongshu-card/
├── SKILL.md                          # 主文件：流程 + 风格识别逻辑
└── references/
    ├── style-luxury-vintage.md       # 风格A：奢华复古
    ├── style-editorial.md            # 风格B：编辑杂志
    ├── style-minimal.md              # 风格C：极简留白
    ├── style-mood.md                 # 风格D/E：图文氛围（明亮+胶片）
    └── layout-templates.md           # 通用HTML骨架和卡片代码模板
```

---

## 常见问题

**Q：导出的 JPG 模糊怎么办？**
A：HTML 文件需要在浏览器中打开（推荐 Chrome），导出时会自动使用 2x 分辨率，实际像素为 2160×2880px，足够清晰。

**Q：没有图片可以用图文风格吗？**
A：可以，Claude 会用渐变色块占位，并在代码注释里告诉你如何替换成自己的图片。

**Q：可以修改颜色和字体吗？**
A：生成的 HTML 文件可以直接编辑，所有样式都在 `<style>` 标签里，结构清晰。

**Q：支持中英文混排吗？**
A：支持，所有风格都搭配了适合中英文混排的字体组合。

---

## 下载

- **GitHub**：[Releases](https://github.com/你的用户名/xiaohongshu-card-skill/releases)
- **网盘**：[链接待更新]

---

## License

MIT — 自由使用和修改，欢迎提 Issue 和 PR 贡献新风格 🎨
