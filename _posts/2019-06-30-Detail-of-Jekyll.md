---
layout: post
title: "Detail-of-Jekyll"
date: 2019-06-30 00:12:15 +0800
tags:
    - "jekyll"
---

目前只是大略了解jeryll的整體流程以及常見class的variable 和 function.但細節還是要按著 [Jekyll official][jekyll-official] 才能完全了解整體的步驟

## MattBlogtheme Tree
現在我們來看在jekyll website(以MattBlogtheme為例的tree)

```
├── 404.html
├── Gemfile
├── Gemfile.lock
├── LICENSE.txt
├── MattBlogtheme.gemspec
├── README.md
├── _config.yml
├── _includes
│   ├── head.html
│   └── sidebar.html
├── _layouts
│   ├── default.html
│   ├── page.html
│   └── post.html
├── _posts
│   ├── 2013-12-31-whats-jekyll.md
│   ├── 2014-01-01-example-content.md
│   ├── 2014-01-02-introducing-lanyon.md
│   ├── 2019-06-23-welcome-to-jekyll.markdown
│   ├── 2019-06-25-HGCAL-input-variable-records.md
│   ├── 2019-06-26-Some-TMVAGuide-notes.md
│   └── 2019-06-30-Detail-of-Jekyll.md
├── _sass
├── _site
│   ├── 2013
│   │   └── 12
│   │       └── 31
│   │           └── whats-jekyll.html
│   ├── 2014
│   │   └── 01
│   │       ├── 01
│   │       │   └── example-content.html
│   │       └── 02
│   │           └── introducing-lanyon.html
│   ├── 2019
│   │   └── 06
│   │       ├── 23
│   │       │   └── welcome-to-jekyll.html
│   │       ├── 25
│   │       │   └── HGCAL-input-variable-records.html
│   │       ├── 26
│   │       │   └── Some-TMVAGuide-notes.html
│   │       └── 30
│   │           └── Detail-of-Jekyll.html
│   ├── 404.html
│   ├── LICENSE.txt
│   ├── MattBlogtheme.gemspec
│   ├── README.md
│   ├── about.html
│   ├── assets
│   │   ├── main.css
│   │   └── minima-social-icons.svg
│   ├── atom.xml
│   ├── feed.xml
│   ├── index.html
│   ├── page2
│   │   └── index.html
│   ├── public
│   │   ├── apple-touch-icon-precomposed.png
│   │   ├── css
│   │   │   ├── lanyon.css
│   │   │   ├── poole.css
│   │   │   └── syntax.css
│   │   └── favicon.ico
│   └── tag
│       ├── HGCAL
│       │   └── index.html
│       └── jekyll
│           └── index.html
├── about.md
├── assets
├── atom.xml
├── index.html
├── public
│   ├── apple-touch-icon-precomposed.png
│   ├── css
│   │   ├── lanyon.css
│   │   ├── poole.css
│   │   └── syntax.css
│   └── favicon.ico
└── tag
    ├── HGCAL
    │   └── index.html
    └── jekyll
        └── index.html
```


<h4>我們先來看看Gemfile:</h4>
在Gemfile中有類似 <span style="color:#ff0000">  gem "(Application)", "-> version"</span>的文字, 之後在安裝 <span style="color:#ff0000">"gem install (Application)"</span>即可

[jekyll-official]: https://jekyllrb.com
