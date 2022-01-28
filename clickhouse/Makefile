.PHONY: config
config:
	rm -rf conf/clickhouse01 conf/clickhouse02 conf/clickhouse03 conf/clickhouse04
	mkdir -p conf/clickhouse01 conf/clickhouse02 conf/clickhouse03 conf/clickhouse04
	REPLICA=01 SHARD=01 envsubst < config.xml > conf/clickhouse01/config.xml
	REPLICA=02 SHARD=01 envsubst < config.xml > conf/clickhouse02/config.xml
	REPLICA=03 SHARD=02 envsubst < config.xml > conf/clickhouse03/config.xml
	REPLICA=04 SHARD=02 envsubst < config.xml > conf/clickhouse04/config.xml
	cp users.xml conf/clickhouse01/users.xml
	cp users.xml conf/clickhouse02/users.xml
	cp users.xml conf/clickhouse03/users.xml
	cp users.xml conf/clickhouse04/users.xml

.PHONY: up
up:
	docker-compose up -d

.PHONY: start
start:
	docker-compose start

.PHONY: down
down:
	docker-compose down
