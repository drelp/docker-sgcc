```shell
sudo docker-compose up -d
sudo docker-compose exec ch_server clickhouse-client


docker run -d --name clickhouse-server --ulimit nofile=262144:262144 yandex/clickhouse-server
docker cp clickhouse-server:/etc/clickhouse-server/ clickhouse-server
```

```shell
show databases;

SHOW DATABASES

Query id: 7b763dc1-1488-4b0a-8462-98346f5b090d

┌─name───────────────┐
│ INFORMATION_SCHEMA │
│ default            │
│ information_schema │
│ system             │
└────────────────────┘

4 rows in set. Elapsed: 0.006 sec.
```

```
docker-compose clickhouse
clickhouse macros
docker-compose zookeeper

https://www.jianshu.com/p/5f7809b1965e
```

```
layer：复制表的层级。在大型集群（比如ClickHouse的发源地Yandex.Metrica）中可能会有多级备份，不过我们自然只有1级了。
shard：实例所持有的分片ID。
replica：实例所持有的副本ID
```