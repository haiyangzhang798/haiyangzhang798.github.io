# 个人学术主页（blogdown + HugoBlox Academic CV，中英双语）

线上地址：`https://haiyangzhang798.github.io/`（英文在 `/`，中文在 `/zh/`）

## 一、需要修改的地方

| 内容 | 文件 |
|---|---|
| 网址 | `config/_default/hugo.yaml` → `baseURL` |
| 网站名称（英文 / 中文） | `config/_default/params.yaml` → `identity.name`；`config/_default/languages.yaml` → `zh.params` |
| 个人资料、教育、经历、奖项、链接（英文） | `data/authors/me.yaml` |
| 个人资料（中文，只写需要翻译的字段） | `data/zh/authors/me.yaml` |
| 头像 | 替换 `assets/media/authors/me.png` |
| 简历 PDF | 放到 `static/uploads/resume.pdf` |
| 主页各板块 | `content/en/_index.md`、`content/zh/_index.md` |
| 导航菜单 | `config/_default/menus.yaml`（英文）、`languages.yaml`（中文） |
| 论文 | `content/{en,zh}/publications/<文件夹>/index.md` |
| 学术报告 | `content/{en,zh}/events/<文件夹>/index.md` |
| 博客 | `content/{en,zh}/post/<文件夹>/index.Rmarkdown` |

中英文版本只要**文件夹名相同**，页面右上角的语言切换就会自动互相跳转。

## 二、本地预览（RStudio）

第一次使用需要安装（Hugo Modules 需要 Go，主题的 Tailwind CSS 需要 Node）：

```bash
brew install go node pnpm
cd ~/Documents/academic-website
pnpm install
```

```r
install.packages("blogdown")
blogdown::install_hugo("0.161.1")   # 与 hugoblox.yaml 中的版本一致
```

之后双击 `academic-website.Rproj` 打开项目：

```r
blogdown::serve_site()      # 实时预览，保存即刷新
blogdown::stop_server()     # 停止预览
blogdown::new_post("My new post", subdir = "post")   # 新建英文文章
blogdown::check_site()      # 检查配置问题
```

> 中文文章：新建后把文件夹移到 `content/zh/post/`，或直接在 `new_post()` 后手动调整路径。
> **注意**：GitHub Actions 不运行 R。`.Rmarkdown` 需要在本地保存/Knit，生成的 `index.markdown` 和 `index_files/` 要一起提交。

> Hugo 0.162.0 与当前主题有兼容问题（引文列表会报 `assignment to entry in nil map`），请先使用 0.161.1。

## 三、发布到 GitHub Pages

1. 在 GitHub 新建**公开**仓库，名字必须是 `haiyangzhang798.github.io`
2. 推送：
   ```bash
   git init -b main
   git add .
   git commit -m "Initial site"
   git remote add origin https://github.com/haiyangzhang798/haiyangzhang798.github.io.git
   git push -u origin main
   ```
3. 仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**
4. 等 Actions 里的 “Deploy website to GitHub Pages” 跑完（约 2 分钟），访问 `https://haiyangzhang798.github.io/`

以后每次 `git push` 都会自动重新构建发布。

## 四、用 BibTeX 批量导入论文（可选）

把导出的 `publications.bib` 放在仓库根目录并推送，Actions 会自动把它转换成 `content/en/publications/` 下的论文页面并提交一个 PR，合并即可。中文版如需要，可把对应文件夹复制到 `content/zh/publications/`。

## 参考

- blogdown 文档：https://bookdown.org/yihui/blogdown/
- HugoBlox 文档：https://docs.hugoblox.com/
