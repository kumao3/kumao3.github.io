---
layout   : single
title    : "Minimal Mistakesのカスタマイズ"
published: true
date     : 2021-01-19 11:30:00 +0900
comments : false
classes: wide
toc: true
categories:
- blog
tags:
- Jekyll
- Github
- Minimal mistakes
---

色々なカスタマイズについてのメモ。

## 記事追加

最初に用意されている`_posts/2021-01-19-welcome-to-jekyll.markdown` を参考に記事を追加していく。

## ロゴ追加

```
mkdir -p assets/images
ロゴデータをasses/images/logo.svgとして作成
```

## toc追加

各記事のYAML Front Matter(先頭行)に追記
```
toc: true
```

* https://mmistakes.github.io/minimal-mistakes/docs/layouts/#table-of-contents

* _config.yml 追記

```
logo: asses/images/logo.svg
```

## ナビゲーション追加(画面上のタブっぽいやつ)


*  `_data/navigation.yml` 用意

```
main:
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

* https://mmistakes.github.io/minimal-mistakes/docs/navigation/
* https://mmistakes.github.io/minimal-mistakes/docs/layouts/#custom-sidebar-navigation-menu
