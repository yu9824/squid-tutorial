# squid-tutorial

cache.logをみるとファイルディスクリプタが足りなくなっているっぽい。

```bash
# ホストOSのファイルディスクリプたを上げる
ulimit -n 65536

# コンテナの起動
docker run -d --name squid -e TZ=Asia/Tokyo -p 3128:3128 ubuntu/squid:6.10-24.10_beta
# docker run -d --ulimit nofile=65536 --name squid -e TZ=Asia/Tokyo -p 3128:3128 ubuntu/squid:6.10-24.10_beta
```
