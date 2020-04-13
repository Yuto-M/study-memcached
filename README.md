# study-memchached

memchachedお試し用repository

### 参考
環境構築の大部分
https://qiita.com/furu8ma/items/10be650bc38b170b8cc6

memchached php公式
https://www.php.net/manual/ja/book.memcached.php

RUN
```
cd study-memchached/docker
docker-compose up -d
~~http://localhost/にアクセス~~
locahost:80でアクセスすると`ERR_CONNECTION_REFUSED`になってchromeでアクセスできないので(curlならちゃんとレスポンス返って来る)
localhost:3000にアクセスする。

chromeだとlocalhost:80が127.0.0.1に割り当てられてないから？(暇だったら調べる)
https://qiita.com/YumaInaura/items/7313feeb26c019fa37ab
```


## memo
### localhost, 127.0.0.1, 0.0.0.0の違い
127.0.0.1 = localhost = ループバックアドレス = host自身
https://qiita.com/1ain2/items/194a9372798eaef6c5ab

### ポート何に使用されているかの確認方法
lsofを使う。
https://do-zan.com/mac-search-using-port/
https://utano.jp/entry/2016/07/mac-and-linux-process-using-port-check-lsof/
```
lsof -i:3000 // 3000番ポートが何に使用されているのか確認する方法
```