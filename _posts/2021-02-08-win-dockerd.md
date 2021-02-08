---
layout   : single
title    : "MacからWindows(wsl2)のDockerデーモンに接続する"
published: true
date     : 2021-02-08 12:00:00 +0900
comments : false
classes: wide
categories:
- blog
tags:
- docker
- wsl2
---

# Docker for Macが重くてつらい

* メモリ16GBのMac Book ProでDocker for Macを起動して作業をしていると、動作も色々もっさりだしファンが回ってうるさいしで、我慢できなくなってきた。
* WindowsのWSL2で動いているDockerdを利用してMacを静かに使いたいなと思ったので設定をしてみた。

## 設定メモ

### Windows側の操作

####  dockerの設定チェックつける

```
Expose daemon on tcp://localhost:2375 without TLS
```

#### windowsにポートフォワードを設定する


* 前提
```
192.168.0.10: 家のLAN内のWindowsにつけた固定IPアドレス
```

上記のDockerでの設定では0.0.0.0ではなくlocalhost:2375でListenするので,192.168.0.10:12375宛のアクセスを127.0.0.1:2375に転送するようにポートフォワードを設定することにした。(13275にしたのはなんとなく。)

```
Mac 192.168.0.9
↓
Windows 192.168.0.10:12375
↓
ポートフォワード
↓
Docker(WSL2) 127.0.0.1:2375
```

```
C:\Windows\system32>netsh interface portproxy add v4tov4 listenport=12375 listenaddr=0.0.0.0 connectport=2375 connectaddress=127.0.0.1

C:\Windows\system32>netsh interface portproxy show all

ipv4 をリッスンする:         ipv4 に接続する:

Address         Port        Address         Port
--------------- ----------  --------------- ----------
0.0.0.0         12375       127.0.0.1       2375

```

#### ファイアウォール設定

* 自分の場合はesetで0.0.0.0:12375への通信を許可。


### Mac側の操作

#### macで環境変数つきでdockerコマンド実行

```
$ DOCKER_HOST=192.168.0.10:12375 docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```



#### 環境変数DOCKER_HOSTの追加

自分のmacではfishを使っているので、

* ~/.config/fish/config.fish

追記
```
set -x DOCKER_HOST 192.168.0.10:12375
```

