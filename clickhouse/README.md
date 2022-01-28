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
```