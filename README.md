# ai-no-legs

> Stay curious, stay real.

一个基于 GitHub Pages 的极简静态文章站。

线上地址：[https://chanthomas20180908-cpu.github.io/ai-no-legs/](https://chanthomas20180908-cpu.github.io/ai-no-legs/)

## 这是什么

`ai-no-legs` 是一个轻量化的文章发布方案。它只用 HTML/CSS 和一个 JSON 清单文件来渲染首页封面图列表，没有构建步骤，没有框架，没有后端。

## 项目结构

```
ai-no-legs/
├── index.html              # 首页 + 文章索引
├── articles/
│   ├── manifest.json       # 文章元数据
│   └── YYYY-MM-DD-slug/    # 每篇文章一个目录
│       ├── index.html      # 文章正文页
│       ├── cover.png       # 首页封面图
│       └── images/         # 正文配图
├── README.md               # 本文件
├── LICENSE                 # 代码授权：MIT
├── LICENSE-content         # 内容授权：CC BY-NC 4.0
│
├── CLAUDE.md               # 给 AI 助手的项目约定 claude（本地-only）
├── AGENTS.md               # 给 AI 助手的项目约定 codex（本地-only）
├── scripts/                # 本地维护脚本（本地-only）
└── docs/                   # 本地维护文档（本地-only）
```

> 注意：`CLAUDE.md`、`scripts/`、`docs/` 被 `.gitignore` 排除，只存在于本地工作副本，不会出现在 GitHub 仓库中。

## 如何新增文章

### 方式一：使用本地脚本（推荐）

如果你本地有 `scripts/add-article.py`：

```bash
cd /Users/test/code/ai-no-legs
python3 scripts/add-article.py
```

按提示输入即可。脚本会自动创建目录、生成 `index.html` 模板、更新 `articles/manifest.json`。

然后手动：
1. 把 `cover.png` 放到文章目录根
2. 把正文图片放到 `images/` 目录
3. 编辑 `index.html`

### 原稿保真

将 Markdown 或其他文章草稿发布为 `index.html` 时，应逐段保留原文的标题、正文、列表、引用、表格、时间戳和落款。HTML 结构、图片路径、封面与 CSS 可以调整；任何润色、删减、重写、数字或引语修改都应先获得作者明确授权。

### 方式二：手动

1. 创建目录：
   ```bash
   mkdir articles/YYYY-MM-DD-your-article-slug
   ```

2. 放入文章文件：
   - `index.html` — 文章正文
   - `cover.png` — 封面图（建议 16:9 或 16:10）
   - `images/` — 正文配图

3. 更新 `articles/manifest.json`：
   ```json
   {
     "slug": "YYYY-MM-DD-your-article-slug",
     "title": "文章标题",
     "date": "YYYY-MM-DD",
     "excerpt": "文章摘要",
     "cover": "articles/YYYY-MM-DD-your-article-slug/cover.png",
     "tags": ["标签1", "标签2"]
   }
   ```

4. 推送 GitHub（见下文"发布"）。

## 本地预览

直接双击 `index.html` 即可查看，或启动本地服务器：

```bash
python3 -m http.server 8000
```

然后访问 `http://localhost:8000`。

## 发布

本地修改完成后，由人类执行以下命令推送到 GitHub：

```bash
git add .
git commit -m "你的提交信息"
git push
```

推送后等待 1-2 分钟，GitHub Pages 会自动刷新。

## 授权

- **站点代码和结构**：[MIT License](./LICENSE)
- **文章、图片及文字内容**：[CC BY-NC 4.0](./LICENSE-content)

## 维护要点

- 文章目录名必须 URL-friendly：`YYYY-MM-DD-slug`。
- 每个文章目录里必须有 `index.html`，GitHub Pages 才能通过目录索引访问。
- 封面图尽量压缩，避免首页加载过慢。
- 修改 HTML 后务必检查属性引号，确保没有中文弯引号。
- 发布草稿前逐项对照原文与 HTML，确保没有非格式性的内容变化。
