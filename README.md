# isucon7q-go

isucon7の予選問題のgo言語環境を起動します


```
dep ensure
docker-compose up -d
```

で起動します

ソースコードなどを修正したら

```
docker-compose restart
```

## 初期データの投入

```sh
git clone github.com/isucon/isucon7-qualify
cd isucon7-qualify
cd bench
./bin/gen-initial-dataset
zcat ./isucon7q-initial-dataset.sql.gz | mysql -uroot -h 0.0.0.0 isubata
```

## ベンチマーク

```sh
git clone github.com/isucon/isucon7-qualify
cd isucon7-qualify
go get github.com/constabulary/gb/...
gb vendor restore
make
./bin/bench -remotes localhost
```

ハッピー チューニング！！