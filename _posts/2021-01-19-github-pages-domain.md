---
layout   : single
title    : ":pig2:github pagesを独自ドメインで置き換え"
published: true
date     : 2021-01-19 12:30:00 +0900
comments : false
classes: wide
categories:
- blog
tags:
- Github pages
- domein
---


##  このブログのurlを置き換えられるかを試す。

```
https://kumao3.github.io
↓
http://blog.koguma.io
```

## セットアップ

### CNAME追加

https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site

```
create a CNAME record that points www.anotherexample.com to <organization>.github.io
```

ということなので、Route53でCNAMEレコードを追加

```
blog.koguma.io CNAME kumao3.github.io
```

* digで確認
```
 dig +short cname blog.koguma.io
 kumao3.github.io.
```

### githubの/settings内にあるcustom domain設定

blog.koguma.ioと入れる。

force httpsにチェックを入れるとhttp://アクセスでhttps://にリダイレクトしてくれる。

ただ、すぐにはチェックをつけられなかった。

```
Enforce HTTPS — Not yet available for your site because the certificate has not finished being issued.
Please allow 24 hours for this process to complete. (blog.koguma.io) 
HTTPS provides a layer of encryption that prevents others from snooping on or tampering with traffic to your site.
When HTTPS is enforced, your site will only be served over HTTPS. Learn more.
```

### 動作確認

* http://blog.koguma.io でサイトがみれた。
* https://blog.koguma.ioだとSSL証明書エラーとなる。