---
image: https://jekyllrb.com/img/octojekyll.png
instantfeedback: true
description: Tạo một blog với Jekyll và đưa lên github
layout: post
title: Tạo blog với Jekyll trên Github
category: Công nghệ
tags: Jekyll, Github, Markdown
keywords: blog, GitHub, Jekyll, Markdown
---

Nếu bạn có thể đọc tài liệu tiếng anh thì xem trên trang chủ của Jekyll, trên đó đã viết rất chi tiết. Vậy nên bài này chỉ dành cho những bạn đọc trên Jekyll rồi mà vẫn chưa làm được.

<figure><img src="https://jekyllrb.com/img/octojekyll.png" alt="Jekyll + Github" title="Jekyll + Github"></figure>

## Tạo repository

Đăng nhập vào Github, tạo một repository mới, đặt tên theo `tenban.github.io`. Trong đó tenban phải trùng với username của bạn tên Github.

## Cấu trúc blog

Ở trên máy tính của bạn, tạo một thư mục tạm, bên trong thư mục tạm tạo thư mục và file theo cấu trúc sau:

```
├── CNAME
├── README.md
├── _config.yml
├── _includes
│   ├── disqus.html
│   ├── footer.html
│   ├── googleanalytics.html
│   ├── header.html
│   └── navside.html
├── _layouts
│   ├── base.html
│   ├── book.html
│   ├── page.html
│   └── post.html
├── _posts
│   ├── Book
│   ├── Life
│   ├── Resource
│   ├── Technology
│   └── Tool
├── index.html
├── pages
│   ├── about.html
│   ├── archive.html
│   └── atom.xml
├── public
│   ├── css
│   ├── fonts
│   ├── img
│   ├── js
│   └── upload
└── sitemap.txt
```

Cấu trúc ở trên được sử dụng trong blog này. Bạn có thể thay đổi một số file hoặc bỏ bớt. Miễn là vẫn đúng cấu trúc như hướng dẫn trên [trang của Jekyll](https://jekyllrb.com/docs/structure/).

Để đơn giản bạn nên clone repository của blog này xuống tại địa chỉ này cho nhanh: 
`https://github.com/RoboWonder/robowonder.github.io.git`

## Cấu hình Jekyll

Mở file `_config.yml` và nhập cấu hình theo mẫu sau, mẫu này dùng trong blog của tôi:

```
# Site settings
title: Blog của Robo Wonder
email: robowonder@outlook.com
description: > # this means to ignore newlines until "baseurl:"
  Blog của Robo Wonder
baseurl: "/" # the subpath of your site, e.g. /blog/
url: http://robowonder.com # the base hostname & protocol for your site
rss_url: /pages/feed.xml
author: Robo Wonder

# Sidebar filter
# Choose 'tag' or 'category' as filter in sidebar.
filter: 'category'
recent_num: 20

# Social account
twitter: robowonder
facebook: robowonder
github: robowonder
instagram: robowonder
linkedin: robowonder

#Ga
ga:
  id: UA-105605074-1
  url: robowonder.com


# avatar and Favicon
avatar: http://graph.facebook.com/100004792424249/picture?width=100&height=100

# Build settings
permalink: /:year/:month/:title.html
markdown: kramdown
highlighter: rouge
mathjax: disabled
sass:
  style: compressed

# Jekyll Plugin
# https://help.github.com/articles/adding-jekyll-plugins-to-a-github-pages-site/
gems:
  - jekyll-sitemap
  - jekyll-seo-tag
  - jekyll-feed

future: true
```

Nếu bạn copy thì nhớ đổi các giá trị phía sau dấu hai chấm (:) cho phù hợp.

## Thêm tên miền vào blog

1. Cấu hình DNS của tên miền về 2 địa chỉ sau:

```
192.30.252.153
192.30.252.154
```

2. Mở file CNAME đã tạo theo cấu trúc hồi nãy lên bằng notepad, nhập domain của bạn vào đó. Ví dụ:

```
robowonder.com
```

## Chỉnh sửa giao diện

Khi bạn đã clone repository của tôi thì giao diện của bạn cũng y xì như của tôi. Nếu bạn muốn đổi lại thì vào sửa lại html của những file trong thư mục `_layouts`

## Up blog lên Github

Nếu bạn biết dùng git thì commit nó lên thôi, còn không biết thì trên Github vẫn có nút upload nhé.


## Viết bài

Vào thư mục `_posts` tạo một file mới và đặt tên theo kiểu `nam-thang-ngay-baiviet.md`, trên cùng của file paste đoạn sau vào. Là header của file:

```
---
layout: post
title: Tạo blog với Jekyll trên Github
category: Công cụ
tags: Jekyll, Github, Markdown
keywords: blog, GitHub, Jekyll, Markdown
---
```

Nhớ sửa lại những thứ sau dấu hai chấm. Bên dưới 3 dấu gạch ngang thì thích gì viết đó, nó là nội dung của bài viết.

Up file này lên thư mục `_posts` trên Github thì bài đăng của bạn sẽ tự động hiển thị. Xong!!!