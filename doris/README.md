```shell script
sudo docker-compose build
sudo docker-compose down
sudo docker-compose up
sudo docker-compose up -d

sudo docker-compose build doris-fe
sudo docker-compose build doris-fe-follower
sudo docker-compose build doris-be
sudo docker-compose build doris-broker

sudo docker-compose up doris-fe
sudo docker-compose up -d doris-fe
sudo docker-compose stop doris-fe
sudo docker-compose rm doris-fe

sudo docker-compose up doris-fe-follower
sudo docker-compose up -d doris-fe-follower
sudo docker-compose stop doris-fe-follower
sudo docker-compose rm -f doris-fe-follower

sudo docker-compose up doris-be
sudo docker-compose up -d doris-be
sudo docker-compose stop doris-be
sudo docker-compose rm doris-be

sudo docker-compose up doris-broker
sudo docker-compose up -d doris-broker
sudo docker-compose stop doris-broker
sudo docker-compose rm doris-broker

cd /home/sgcc/docker-sgcc/doris

sudo docker-compose up -d prometheus
sudo docker-compose stop prometheus
sudo docker-compose rm prometheus

sudo docker-compose up -d grafana-mysql80
sudo docker-compose stop grafana-mysql80
sudo docker-compose rm grafana-mysql80

sudo docker-compose up grafana
sudo docker-compose up -d grafana
sudo docker-compose stop grafana
sudo docker-compose rm grafana

sudo docker-compose logs -f grafana

sudo docker-compose up kettle
sudo docker-compose up -d kettle
sudo docker-compose stop kettle
sudo docker-compose rm kettle

sudo docker-compose up sgcc-mongo
sudo docker-compose up -d sgcc-mongo
sudo docker-compose stop sgcc-mongo
sudo docker-compose rm sgcc-mongo

sudo docker-compose up sgcc-mongo-express
sudo docker-compose up -d sgcc-mongo-express
sudo docker-compose stop sgcc-mongo-express
sudo docker-compose rm sgcc-mongo-express

sudo docker-compose up sgcc-mysql
sudo docker-compose up -d sgcc-mysql
sudo docker-compose stop sgcc-mysql
sudo docker-compose rm sgcc-mysql

sudo docker-compose up sgcc
sudo docker-compose up -d sgcc
sudo docker-compose stop sgcc
sudo docker-compose rm sgcc

tail -f data/fe/log/fe.*
tail -f data/be/log/be.*

docker exec -it 1055d4412078 bash
mysql -h127.0.0.1 -uroot -p
mysql -h10.50.10.27 -ugrafana -p

mysql -h127.0.0.1 -uroot -p -P9030
mysql -h10.50.10.27 -uroot -p -P9030
sgcc
ALTER SYSTEM ADD BACKEND "10.50.10.27:9050";

ALTER SYSTEM DROPP BACKEND "10.50.10.27:9050";
ERROR 1064 (HY000): errCode = 2, detailMessage = It is highly NOT RECOMMENDED to use DROP BACKEND stmt.It is not safe to directly drop a backend. All data
on this backend will be discarded permanently. If you insist, use DROPP BACKEND stmt (double P).

ALTER SYSTEM ADD BACKEND "10.50.10.27:9050";

ALTER SYSTEM ADD BROKER hdfs_broker "10.50.10.27:8000";
SHOW PROC '/brokers';

SHOW PROC '/backends';
SHOW PROC '/backends'\G
ALTER SYSTEM ADD OBSERVER "10.50.10.27:9010";
SHOW PROC '/frontends';
SHOW PROC '/frontends'\G
SET PASSWORD FOR 'root' = PASSWORD('sgcc');
CREATE DATABASE example_db;
CREATE USER 'test' IDENTIFIED BY 'test';
SHOW DATABASES;
GRANT ALL ON example_db TO test;
HELP CREATE TABLE;
USE example_db;
CREATE TABLE table1
(
    siteid INT DEFAULT '10',
    citycode SMALLINT,
    username VARCHAR(32) DEFAULT '',
    pv BIGINT SUM DEFAULT '0'
)
AGGREGATE KEY(siteid, citycode, username)
DISTRIBUTED BY HASH(siteid) BUCKETS 10
PROPERTIES("replication_num" = "1");
SHOW TABLES;
DESC table1;
```

```shell script
sudo docker network create --subnet=172.19.0.0/16 sgcc-network
```

```shell script
http://doris.incubator.apache.org/master/zh-CN/administrator-guide/operation/monitor-alert.html
https://prometheus.io/download/
https://grafana.com/grafana/download
http://doris.incubator.apache.org/master/zh-CN/installing/install-deploy.html#%E9%9B%86%E7%BE%A4%E9%83%A8%E7%BD%B2
/etc/prometheus/prometheus.yml
/etc/grafana/grafana.ini

/usr/share/grafana

create database grafana DEFAULT CHARACTER SET utf8mb4;
create user 'grafana'@'127.0.0.1' identified by 'grafana';
grant all privileges on grafana.* to 'grafana'@'127.0.0.1';
create user 'grafana'@'%' identified by 'grafana';
grant all privileges on grafana.* to 'grafana'@'%';
flush privileges;

use grafana

CREATE TABLE `session` (
    `key`       CHAR(16) NOT NULL,
    `data`      BLOB,
    `expiry`    INT(11) UNSIGNED NOT NULL,
    PRIMARY KEY (`key`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

insert into table1(siteid,citycode,username,pv) values (1,'1','1',1);
select * from table1;

chown -R root:root /etc/grafana && \
chmod -R a+r /etc/grafana && \
chown -R grafana:grafana /var/lib/grafana && \
chown -R grafana:grafana /usr/share/grafana

rm -rf data/
git reset --hard

https://cloud.baidu.com/doc/DORIS/s/pkmealpi3

{"receivedBytes":0,"errorRows":0,"committedTaskNum":0,"loadedRows":0,"loadRowsRate":0,"abortedTaskNum":138,"totalRows":0,"unselectedRows":0,"receivedBytesRate":0,"taskExecuteTimeMs":1}
```