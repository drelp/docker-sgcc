```shell
sudo docker-compose -f docker-compose-distributed-local.yml up
sudo docker-compose -f docker-compose-distributed-local.yml logs

sudo docker-compose -f docker-compose-distributed-local.yml up -d namenode
sudo docker-compose -f docker-compose-distributed-local.yml up -d datanode
sudo docker-compose -f docker-compose-distributed-local.yml down

sudo docker build -t='yiluxiangbei/hbase:2.4.9' -f Dockerfile .

sudo docker-compose up -d hbase-master
sudo docker-compose stop hbase-master

sudo docker-compose up -d
sudo docker-compose down
sudo docker-compose logs -f

http://10.50.10.27:16010/
```

```
https://hub.docker.com/r/coomia/hbase2.2/tags?page=1&ordering=last_updated
https://hub.docker.com/r/pierrezemb/hbase-docker

docker run -itd         -p 8080:8080         -p 9090:9090         -p 2181:2181         -p 16000:16000         -p 16010:16010         -p 16020:16020         -p 16030:16030  --name hbase  coomia/hbase2.2:0.1

https://github.com/warp-poke/hbase-helm

ssh-keygen -t rsa -C '1097692918@qq.com'

https://hbase.apache.org/book.html
http://hbase.org.cn/docs/32.html
```

```
hbase 2.0.3
flink 1.12.0
clickhouse 21.9.4.35
elasticsearch 7.13.4

k8s hbase
k8s hbase 集群
hbase helm
docker-compose hbase
docker-compose zookeeper
docker-compose hadoop
```