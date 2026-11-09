# smallpig

个人技术博客，纯静态 HTML + CSS，无框架、无构建步骤。

线上地址：<https://smallpig.dpdns.org>

## 结构

```
.
├── index.html              首页（文章列表）
├── about.html              关于页
├── styles.css              全站样式（含深色模式）
├── 404.html                找不到页面时的兜底
└── posts/
    ├── hello-world.html    示例文章
    └── c-toolchain.html    示例文章
```

## 怎么加一篇新文章

1. 复制 `posts/hello-world.html`，重命名成英文短横线格式，例如 `posts/pointers.html`
2. 改里面的 `<title>`、`<h1>`、`<time datetime="YYYY-MM-DD">`、正文
3. 在 `index.html` 的 `<ul class="post-list">` 里加一条：

```html
<li>
  <a class="post-title" href="/posts/pointers.html">指针到底难在哪</a>
  <time datetime="2026-11-15">2026-11-15</time>
  <p class="post-summary">一句话摘要。</p>
</li>
```

4. `git add . && git commit -m "post: 指针到底难在哪" && git push`

推上去大约 30 秒后 Cloudflare Pages 自动构建发布，不用手动上传。

## 部署

- 托管：Cloudflare Pages
- 构建命令：留空
- 输出目录：`/`（根目录）
- 自定义域名：`smallpig.dpdns.org`（NS 指向 `michael.ns.cloudflare.com` / `ursula.ns.cloudflare.com`）

## 本地预览

直接双击 `index.html` 就能看，但 `styles.css` 用的是绝对路径 `/styles.css`，
所以更推荐起个本地服务器：

```bash
python -m http.server 8000
# 然后打开 http://localhost:8000
```
