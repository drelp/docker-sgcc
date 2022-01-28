```shell
sudo docker-compose up
sudo docker-compose up -d
sudo docker-compose exec ch_server clickhouse-client

docker run -d --name clickhouse-server --ulimit nofile=262144:262144 yandex/clickhouse-server
docker cp clickhouse-server:/etc/clickhouse-server/ clickhouse-server

make config
make config up
docker-compose -f docker-compose-local.yml rm
sudo docker-compose -f docker-compose-local.yml up
sudo docker-compose -f docker-compose-local.yml up -d

sudo docker-compose -f docker-compose-local.yml exec clickhouse01 clickhouse-client

docker run -d -p 8080:80 spoonest/clickhouse-tabix-web-client

http://10.50.10.27:8090/
http://ch_server:8123
default

PASSWORD=$(base64 < /dev/urandom | head -c8); echo "123456"; echo -n "123456" | sha256sum | tr -d '-'
123456
8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92

PASSWORD=$(base64 < /dev/urandom | head -c8); echo "888888"; echo -n "888888" | sha256sum | tr -d '-'
888888
92925488b28ab12584ac8fcaa8a27a0f497b2c62940c8f4fbc8ef19ebc87c43e
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

select * from system.clusters\G

CREATE DATABASE company_db ON CLUSTER 'company_cluster';

CREATE TABLE company_db.events ON CLUSTER 'company_cluster' ( \
    time DateTime, \
    uid  Int64, \
    type LowCardinality(String) \
) \
ENGINE = ReplicatedMergeTree('/clickhouse/tables/{cluster}/{shard}/table', '{replica}') \
PARTITION BY toDate(time) \
ORDER BY (uid);

CREATE TABLE company_db.events_distr ON CLUSTER 'company_cluster' AS company_db.events \
ENGINE = Distributed('company_cluster', company_db, events, uid);
```

```
docker-compose clickhouse
clickhouse macros
docker-compose zookeeper

https://www.jianshu.com/p/5f7809b1965e
https://github.com/tabixio/tabix
https://zhuanlan.zhihu.com/p/268857326
```

```
layer：复制表的层级。在大型集群（比如ClickHouse的发源地Yandex.Metrica）中可能会有多级备份，不过我们自然只有1级了。
shard：实例所持有的分片ID。
replica：实例所持有的副本ID
```