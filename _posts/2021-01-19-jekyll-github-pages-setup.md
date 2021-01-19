# ブログサイトをgithub pagesで公開する

jekyll(`theme:minimal-mistakes`)でgithub pagesにブログを公開しようと思い、
その環境構築をしたときのメモ。

## セットアップ

* githubでのレポジトリを作成する。`kumao3.github.io`
* git cloneしてclone先ディレクトリに移動。
* jekyllプロジェクト?作成

```
$ bundle install jekyll -v=3.9.0
$ jekyklll new .
```
* bundle install

```
Gemfile
---
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
---

$ bundle install
```


* _config.yml

  * `remote_theme: "mmistakes/minimal-mistakes@4.21.0"`　置き換え
  * `plugins: jekyll-include-cache` 追記

```
title: Your awesome title
email: your-email@example.com
description: >- # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: jekyllrb
github_username:  jekyll

# Build settings
markdown: kramdown
#theme: minima
remote_theme: "mmistakes/minimal-mistakes@4.21.0"
plugins:
  - jekyll-feed
  - jekyll-include-cache

# Exclude from processing.
# The following items will not be processed, by default. Create a custom list
# to override the default setting.
# exclude:
#   - Gemfile
#   - Gemfile.lock
#   - node_modules
#   - vendor/bundle/
#   - vendor/cache/
#   - vendor/gems/
#   - vendor/ruby/
```

*  githubに git push

```
git add -A ; git commit -m update ; git push
```


* github pagesに反映されたかブラウザで確認
  * https://{username}.github.io/ 
  * https://kumao3.github.io/