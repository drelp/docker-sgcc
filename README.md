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

http://10.50.10.27:8030/login
root
sgcc

sudo docker-compose up -d prometheus

```