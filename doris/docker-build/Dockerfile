FROM apachedoris/doris-dev:build-env-1.2

RUN mkdir -p /home/doris

# ENV JAVA_HOME /usr/lib/jvm/java
# /usr/java/jdk

ENV TZ Asia/Shanghai
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

# 0.12.21
COPY ./fe/ /home/doris/fe

COPY ./be/ /home/doris/be

COPY ./apache_hdfs_broker/ /home/doris/fs_broker

EXPOSE 8030 9020 9030 9010 9070 9060 8060 8040 9050 8000

VOLUME ["/home/doris/fe/conf", "/home/doris/fe/log", "/home/doris/fe/doris-meta", "/home/doris/be/conf", "/home/doris/be/log", "/home/doris/be/storage", "/home/doris/fs_brokers/conf"]

COPY entrypoint.sh /home/doris

RUN chmod +x /home/doris/entrypoint.sh

ENV DORIS_HOME /home/doris

ENTRYPOINT ["/home/doris/entrypoint.sh"]
