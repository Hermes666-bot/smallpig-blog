# smallpig

学习笔记 + 生活札记。纯静态 HTML + CSS，无框架、无构建步骤。

线上地址：<https://smallpig.dpdns.org>

> 在坚冰还盖着北海的时候，我看到了怒放的梅花.

## 结构

```
.
├── index.html     首页（标题、文章列表）
├── about.html     关于页
├── styles.css     全站样式（含深色模式、题记样式）
└── 404.html       找不到页面时的兜底
```

> `posts/` 目录会在写第一篇文章时创建。目前还没文章。

## 怎么加一篇新文章

**第 1 步**：在根目录新建 `posts/` 文件夹，在里面新建文件，用英文短横线命名，比如 `posts/pointers.html`。

**第 2 步**：把下面的模板粘进去，改标题、日期、正文：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>文章标题 · smallpig</title>
<link rel="stylesheet" href="/styles.css">
</head>
<body>
<header class="site-header">
  <a class="brand" href="/">smallpig</a>
  <nav>
    <a href="/about">关于</a>
    <a href="https://github.com/Hermes666-bot" rel="noopener noreferrer">GitHub</a>
  </nav>
</header>

<main>
  <article>
    <a class="back-link" href="/">← 返回首页</a>
    <h1>文章标题</h1>
    <time datetime="2026-11-10">2026-11-10</time>

    <p>正文第一段……</p>

    <h2>小标题</h2>
    <p>正文……</p>

    <pre><code>代码块</code></pre>
  </article>
</main>

<footer class="site-footer">
  <p class="epigraph">在坚冰还盖着北海的时候，我看到了怒放的梅花.</p>
  <p>© 2026 刘东昊 · <a href="https://smallpig.dpdns.org">smallpig.dpdns.org</a></p>
</footer>
</body>
</html>
```

**第 3 步**：把 `index.html` 里的 `<p class="empty-note">还没有文章。</p>` 换成文章列表：

```html
<ul class="post-list">
  <li>
    <a class="post-title" href="/posts/pointers">指针到底难在哪</a>
    <time datetime="2026-11-10">2026-11-10</time>
    <p class="post-summary">一句话摘要。</p>
  </li>
</ul>
```

> 注意链接写 `/posts/pointers`（不带 `.html`），Cloudflare Pages 会自动处理。

**第 4 步**：发布。

```bash
git add . && git commit -m "post: 指针到底难在哪" && git push
```

推上去 30–60 秒后 Cloudflare Pages 会自动构建部署，不需要手动上传。

## 部署

- 托管：Cloudflare Pages
- 构建命令：留空
- 输出目录：`/`（根目录）
- 自定义域名：`smallpig.dpdns.org`（NS 指向 `michael.ns.cloudflare.com` / `ursula.ns.cloudflare.com`）

## 本地预览

直接双击 `index.html` 也能看，但 `styles.css` 用的是绝对路径 `/styles.css`，所以更推荐起个本地服务器：

```bash
python -m http.server 8000
# 然后打开 http://localhost:8000
```

## 备忘

- 域名 2027-11-09 到期，**到期前 120 天内**（2027 年 7 月中旬起）去 DigitalPlat 后台手动点「免费续费」，**不会自动续**
- 大文件（视频、压缩包）不要进 git，先加 `.gitignore`
