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
mysql -h10.50.10.27 -uroot -p -P3316
root

create database sgcc default character set utf8mb4 collate utf8mb4_general_ci;
create database dataease default character set utf8mb4 collate utf8mb4_general_ci;

update datasource set configuration='FGdni+RMR0cExlN1RYXIvy2vSKiJEFy23jOVIhIZOZte8V7lXdroyPseLVepG4N5uOfohY4OCuTOi0qVuWOFDrnFOePJePzLQPyqAtwP9miq4gFbD4ecWbGg3oQ/2bld7s7NxgNShDMFQlMM9qTG2FL12TNLPVsVD2Xa4Pbf0NMXU+TDUoZ8DETgKl1JCopmtc1UW+Y3DS0u2ABIS6ffA+mnRSykZp68nQIeOufWpk4IyJ5rutcO5hhKnmpmXjFyNKqv7o/q+YGjjxekRjLH4xjai2oWBpYqbWx7Isf9zpUptocJkpbEEf7AV+nu6nGFA5rYkodxAI2QOUbM5UbQN8q8KE6KiDZeH1yqSceN4SOnppqPyTZbUbdLAhR+nAfy1td+0NzH6iWH9UckaJSNUogeUw6BiY+VETgY6bZq2/UTGS45oD8Ug3Vb5D5avbzOSrEaq9WG+SQ6GIE9dS71YdtdkGVgSDdTLtnYZYj5xZE=' where name='demo';

sudo docker-compose up sgcc
sudo docker-compose up -d sgcc
sudo docker-compose stop sgcc

http://10.50.10.27:8061/
demo
dataease

sudo docker-compose up -d sgcc-mongodb
sudo docker-compose up -d sgcc-mongo-express

http://10.50.10.27:8081/

https://sgcc-bj.7otech.com
demo
Sgcc2022

admin
Sgcc2022

10.50.10.27
9030

蠃鱼数据中台

https://cdkm.com/cn/png-to-svg
```