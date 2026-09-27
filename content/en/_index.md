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
        text: Download CV
        url: uploads/resume.pdf   # 把简历放到 static/uploads/resume.pdf
      headings:
        about: 'About Me'
        education: 'Education'
        interests: 'Interests'
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
      title: 'Research'
      subtitle: ''
      text: |-
        My research sits at the intersection of **XXX** and **XXX**. I am particularly interested in:

        - Topic one — one sentence on the question you study
        - Topic two — one sentence on methods or data
        - Topic three — one sentence on applications

        I am always open to collaboration. Feel free to [reach out](mailto:you@example.edu).
    design:
      columns: '1'

  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2

  - block: collection
    content:
      title: Publications
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
      title: Recent & Upcoming Talks
      filters:
        folders:
          - events
    design:
      view: card

  - block: collection
    id: news
    content:
      title: Recent Posts
      count: 5
      filters:
        folders:
          - post
      order: desc
    design:
      view: card
---
