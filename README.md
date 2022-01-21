# docker-sgcc

```shell
cp -r PALO-0.14.13-release-no-avx2-binary/be doris/docker-build/
cp -r PALO-0.14.13-release-no-avx2-binary/fe/ doris/docker-build/
cp -r PALO-0.14.13-release-no-avx2-binary/apache_hdfs_broker/ doris/docker-build/

cd doris/docker-build
sudo docker build -f Dockerfile -t doris-sgcc:v1.0 .

sudo docker-compose up -d doris-fe
sudo docker-compose up -d doris-be

mysql -h127.0.0.1 -uroot -p -P9030
SET PASSWORD FOR 'root' = PASSWORD('sgcc');

mysql -h127.0.0.1 -uroot -p -P9030
sgcc
ALTER SYSTEM ADD BACKEND "10.50.10.27:9050";
SHOW PROC '/backends';

CREATE DATABASE sgcc;

http://10.50.10.27:8030/login
root
sgcc

sudo docker-compose up -d prometheus
http://10.50.10.27:9090

sudo docker-compose up -d grafana-mysql80
mysql -h127.0.0.1 -uroot -p
root

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

sudo docker-compose up -d grafana

http://10.50.10.27:3000
admin
admin

sgcc2022

add datasource
import json file

sudo docker-compose up -d kettle

docker-compose logs -f

sudo docker-compose up -d sgcc-mysql
mysql -h127.0.0.1 -uroot -p -P3316
root

create database sgcc default character set utf8mb4 collate utf8mb4_unicode_ci;

sudo docker-compose up -d sgcc
```