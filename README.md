# docker-sgcc

```shell
cp -r PALO-0.14.13-release-no-avx2-binary/be doris/docker-build/
cp -r PALO-0.14.13-release-no-avx2-binary/fe/ doris/docker-build/
cp -r PALO-0.14.13-release-no-avx2-binary/apache_hdfs_broker/ doris/docker-build/

cd doris/docker-build
sudo docker build -f Dockerfile -t doris-sgcc:v1.0 .
```