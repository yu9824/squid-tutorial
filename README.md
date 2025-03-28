# squid-tutorial

## TODO
cache.logをみるとファイルディスクリプタが足りなくなっているっぽい。
なんとかしたい。

ホストOS, コンテナ, コンテナのOSのファイルディスクリプタをあげたつもりだけどうまくいかなかった。WindowsとMacで違う？

```bash
# ホストOSのファイルディスクリプたを上げる
ulimit -n 65536

# コンテナの起動
docker run -d --name squid -e TZ=Asia/Tokyo -p 3128:3128 ubuntu/squid:6.10-24.10_beta
# コンテナのファイルディスクリプタを上げる場合、
# docker run -d --ulimit nofile=65536 --name squid -e TZ=Asia/Tokyo -p 3128:3128 ubuntu/squid:6.10-24.10_beta
# 本番 (自動リスタート)
# docker run -d --ulimit nofile=65536 --restart=always --name squid -e TZ=Asia/Tokyo -p 3128:3128 ubuntu/squid:6.10-24.10_beta
```

## テスト方法

```bash
curl -v -x http://localhost:3128 https://www.google.co.jp

```
