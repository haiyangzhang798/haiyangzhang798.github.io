# blogdown 设置（在 RStudio 打开本项目时自动加载）
# 参考：https://bookdown.org/yihui/blogdown/global-options.html
if (file.exists("~/.Rprofile")) sys.source("~/.Rprofile", envir = environment())

options(
  # 与 hugoblox.yaml 和 GitHub Actions 中的 Hugo 版本保持一致
  blogdown.hugo.version = "0.161.1",
  # 新建文章默认用 .Rmarkdown（输出 Markdown，公式和代码高亮交给 Hugo 主题处理）
  blogdown.ext = ".Rmarkdown",
  # 新文章放在页面包（文件夹）里：content/en/post/<slug>/index.Rmarkdown
  blogdown.new_bundle = TRUE,
  blogdown.subdir = "post",
  blogdown.author = "me",
  # 保存 .Rmarkdown 时自动 knit；打开项目时不自动启动预览
  blogdown.knit.on_save = TRUE,
  blogdown.serve_site.startup = FALSE
)
