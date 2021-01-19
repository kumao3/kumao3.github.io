---
layout   : single
title    : "Minimal Mistakesのカスタマイズ"
published: true
date     : 2021-01-19 11:10:00 +0900
comments : false
categories:
- ブログ
tags:
- Jekyll
- Github
- Minimal mistakes
---

最初に用意されている`_posts/2021-01-19-welcome-to-jekyll.markdown` を参考に記事を追加していく。


## ロゴ追加

```
mkdir -p assets/images
ロゴデータをasses/images/logo.svgとして作成
```

* _config.yml 追記

```
logo: asses/images/logo.svg
```

## サイドバー追加


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
