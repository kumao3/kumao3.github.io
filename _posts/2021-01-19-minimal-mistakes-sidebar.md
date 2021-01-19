---
layout   : single
title    : "Minimal Mistakesのカスタマイズ"
published: true
date     : 2021-01-19 11:30:00 +0900
comments : false
classes: wide
categories:
- blog
tags:
- Jekyll
- Github
- Minimal mistakes
---

色々なカスタマイズについてのメモ。

ここを参考にする。

https://mmistakes.github.io/minimal-mistakes/docs/configuration/


## 記事追加

最初に用意されている`_posts/2021-01-19-welcome-to-jekyll.markdown` を参考に記事を追加していく。


## サイトの設定

#### ロゴ変更

* ロゴファイル追加
```
mkdir -p assets/images
ロゴデータをasses/images/logo.svgとして作成
```

* _config.yml追記 
```
logo: asses/images/logo.svg
```

#### author追加
  * `_data/authors.yml`用意

```
kumao:
  name        : "kumao"
  bio         : "What do you want, jewels? I am a very extravagant man."
  avatar      : "/assets/images/me.jpg"
  links:
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      url: "https://twitter.com/tweetrade"
```

#### サイドバーにナビ
  *  `_data/navigation.yml` 用意

```
docs:
  - title: "Quick-Start Guide"
    url: /docs/quick-start-guide/
  - title: "Posts"
    url: /year-archive/
  - title: "Categories"
    url: /categories/
  - title: "Tags"
    url: /tags/
  - title: "Pages"
    url: /page-archive/
  - title: "Collections"
    url: /collection-archive/
  - title: "External Link"
    url: https://google.com
```

### 記事のデフォルトスタイル設定

* _config.yml

```
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: wide
      toc: false
      author: kumao
      author_profile: true
      read_time: true
      comments: true
      share: true
      related: true
      sidebar:
        nav: "docs"
```


