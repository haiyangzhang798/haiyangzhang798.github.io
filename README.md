# 张海洋 个人学术主页（blogdown + 自定义 Hugo 主题，中英双语）

网址：https://haiyangzhang-lab.com （英文在 `/`，中文在 `/zh/`）

风格参考 Google Sites 经典布局：顶部大幅横幅 + 白框标题、透明导航栏、首页左图右文。
主题完全写在本项目的 `layouts/` 和 `assets/css/main.css` 里，**不依赖 Go、Node 或任何外部 CDN**，
字体和公式渲染（KaTeX）都已放在本地，国内访问更快。

## 改内容去哪里

| 想改的内容 | 文件 |
|---|---|
| 顶部横幅图 | 替换 `static/images/banner.jpg`（建议 2400×800 左右的横向风景照） |
| 首页词云 | 替换 `static/images/wordcloud.jpg` |
| 个人照片 | 替换 `assets/media/authors/me.jpg` |
| 姓名、简介、教育/工作经历、奖项（英文） | `data/authors/me.yaml` |
| 同上（中文） | `data/zh/authors/me.yaml` |
| 论文列表（中英文共用） | `data/publications.yaml`（`featured: true` 的会显示在 Research 页） |
| 学术链接、邮箱、简历 PDF | `config/_default/params.yaml` |
| 研究方向页 | `content/en/research.md`、`content/zh/research.md` |
| 课题组页（成员照片放 `static/images/people/`） | `content/en/group.md`、`content/zh/group.md` |
| 联系方式页 | `content/en/contact.md`、`content/zh/contact.md` |
| 导航菜单 | `config/_default/menus.en.yaml`、`menus.zh.yaml` |
| 颜色、字体、版式 | `assets/css/main.css` 顶部的 `:root` 变量 |

单个页面想用不同横幅图：在该页 front matter 里加 `banner: images/xxx.jpg`。

## 本地预览（RStudio）

只需要 Hugo，不再需要 Go / Node / pnpm：

```r
blogdown::install_hugo("0.161.1")   # 首次
blogdown::serve_site()              # 预览，保存即刷新
blogdown::stop_server()
```

## 写博客（R Markdown）

```r
blogdown::new_post("文章标题", subdir = "post", ext = ".Rmarkdown")
```

新文章默认在 `content/en/post/`；中文文章把文件夹移到 `content/zh/post/`。
保存/Knit 后，把生成的 `index.markdown` 和 `index_files/` 一起提交（GitHub 上的构建不运行 R）。

## 发布

```bash
git add -A
git commit -m "更新网站"
git push
```

推送后 GitHub Actions 自动构建发布（仓库 Settings → Pages → Source 需为 **GitHub Actions**）。
