# 个人博客系统

个基于 Jekyll + Minimal Mistakes 的个人博客站点，重点放在可维护性上：内容、配置、布局和样式分层管理，便于后续持续写作和扩展。

## 代码结构

```text
.
├── _config.yml              # 站点配置、主题、默认值、归档设置
├── _data/
│   └── navigation.yml       # 顶部导航
├── _includes/               # 自定义 include，覆盖主题默认片段
│   ├── breadcrumbs.html     # 面包屑导航
│   ├── category-list.html   # 分类链接锚点
│   ├── page__date.html      # 页面日期展示
│   ├── page__meta.html      # 文章/页面元信息
│   ├── post-timeline.html   # 首页时间轴
│   ├── rendered-post-date.html  # 统一日期来源
│   └── tag-list.html        # 标签链接锚点
├── _layouts/
│   └── single.html          # 文章/页面布局覆盖
├── _pages/
│   ├── about.md             # 关于页面
│   ├── categories.md        # 分类归档
│   └── 404.md               # 404 页面
├── _posts/                  # 正文文章
├── assets/
│   └── css/main.scss        # 站点样式入口
├── Gemfile                  # Ruby 依赖
└── README.md                # 使用说明
```

## 当前功能

站点当前保留的核心能力是：

- 首页时间轴展示最近文章。
- 文章页、归档页、分类页和标签页正常工作。

## 本地调试

1. 安装 Ruby 依赖：`bundle install`
2. 启动本地预览：`bundle exec jekyll serve --livereload`
3. 打开 `http://localhost:4000`

## 写作方式

1. 新建文章到 `_posts/`，文件名使用 `YYYY-MM-DD-slug.md`。
2. 在文章头部填写标题、分类和标签。
3. 文章会自动进入首页时间轴、分类页和标签页。

文章示例：

```yaml
---
title: "第一篇文章"
date: 2026-05-25 09:00:00 +0800
categories:
  - 日志
tags:
  - Jekyll
  - Minimal Mistakes
---
```

## 架构说明

这个仓库采用“配置、页面、布局、片段、文章、样式”六层拆分：

- `_config.yml` 负责站点级设置，包括主题、默认布局、归档路径、作者信息和日期格式。
- `_data/navigation.yml` 集中控制导航，减少页面里重复写链接。
- `_layouts/` 放布局级覆盖，当前主要用于 `single` 页面的统一渲染。
- `_includes/` 放可复用片段，当前用于时间轴、面包屑、日期和元信息渲染。
- `_pages/` 放固定页面，便于统一管理首页、关于、归档页等入口。
- `_posts/` 只放内容，不混入站点结构逻辑。
- `assets/css/main.scss` 是样式入口，负责站点层的样式扩展。

## 后续建议

1. 把作者信息、头像和社交链接替换成你的真实资料。
2. 继续补充正式文章，并逐步稳定分类和标签体系。
3. 如果以后还想加评论或在线写作，再单独作为独立模块接回。
