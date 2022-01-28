```shell
chmod -R 777 es01 es02 es03

vi /etc/sysctl.conf
vm.max_map_count=262144
/sbin/sysctl -p

docker-compose -f docker-compose-local.yml rm
sudo docker-compose -f docker-compose-local.yml up
sudo docker-compose -f docker-compose-local.yml up -d
```

```
docker-compose elasticsearch
```