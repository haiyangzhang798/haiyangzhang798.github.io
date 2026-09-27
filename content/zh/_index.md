---
# 主页 / Homepage — 由若干 "block" 组成，可增删调序
title: ''
summary: ''
date: 2026-09-27
type: landing

sections:
  - block: resume-biography-3
    content:
      username: me          # 对应 data/authors/me.yaml
      text: ''
      button:
        text: 下载简历
        url: uploads/resume.pdf   # 把简历放到 static/uploads/resume.pdf
      headings:
        about: '关于我'
        education: '教育经历'
        interests: '研究兴趣'
    design:
      background:
        gradient_mesh:
          enable: true
      name:
        size: md
      avatar:
        size: medium
        shape: circle

  - block: markdown
    content:
      title: '研究方向'
      subtitle: ''
      text: |-
        我的研究聚焦于 **XXX** 与 **XXX** 的交叉领域，主要关注：

        - 方向一：一句话说明你研究的问题
        - 方向二：一句话说明所用方法或数据
        - 方向三：一句话说明应用场景

        欢迎交流合作，请[发邮件联系我](mailto:you@example.edu)。
    design:
      columns: '1'

  - block: collection
    id: papers
    content:
      title: 代表性论文
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2

  - block: collection
    content:
      title: 论文发表
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation

  - block: collection
    id: talks
    content:
      title: 学术报告
      filters:
        folders:
          - events
    design:
      view: card

  - block: collection
    id: news
    content:
      title: 最新文章
      count: 5
      filters:
        folders:
          - post
      order: desc
    design:
      view: card
---
