FROM openjdk:8-jdk
ARG SSH_PUB='ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDZm6TySF6CmS9psbbgT/Oy2+CR+sU9woemErYBe7zPxaAH7ElFGmHNTF5LmFNSa/qrJmw+3PWghmKEQglhue9mTuKf5FABLuYY+UGgvyP/lpeg8DeMSDwrMEaRK9UCT+tjsdOnprmdIlkxJBcE3DdXoICLMzhZGwtEZGQ5qaEZOlyc0S3KsFI0MpdvK74T0dGJ4CjvEg7h1tKKjXQvlpFMQ8bP8lsYt2IwDk7oW9XQjm2vGSbKLX9+Z3S8HY9NDg/ianng0vqpOgFUenwttCsrp+qB0//QU7+vrkm3PaCB8KcSxg/R0fcP32/3q6OvWFUwUQVicmkX5/z/1A+ak4nN 1097692918@qq.com'
RUN apt-get update;
RUN apt-get install -y openssh-server net-tools vim git;
RUN sed -i -r 's/^\s*UseDNS\s+\w+/#\0/; s/^\s*PasswordAuthentication\s+\w+/#\0/; s/^\s*ClientAliveInterval\s+\w+/#\0/' /etc/ssh/sshd_config;
RUN echo 'UseDNS no \nPermitRootLogin yes \nPasswordAuthentication yes \nClientAliveInterval 30' >> /etc/ssh/sshd_config;
RUN cat /etc/ssh/sshd_config
RUN su root bash -c 'cd;mkdir .ssh;chmod 700 .ssh;echo ${SSH_PUB} > .ssh/authorized_keys;chmod 644 .ssh/authorized_keys'
RUN su root bash -c 'cd;ssh-keygen -t rsa -f ~/.ssh/id_rsa; cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys'

# hadoop
ENV HADOOP_TGZ_URL=https://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-3.2.2/hadoop-3.2.2.tar.gz
ENV HADOOP_HOME=/opt/hadoop
ENV PATH=$HADOOP_HOME/bin:$PATH
RUN set -ex; \
    mkdir -p $HADOOP_HOME; \
    wget -nv -O $HADOOP_HOME/src.tgz $HADOOP_TGZ_URL; \
    tar -xf $HADOOP_HOME/src.tgz --strip-components=1 -C $HADOOP_HOME; \
    rm $HADOOP_HOME/src.tgz; \
    chown -R root:root $HADOOP_HOME;

# clean trash file or dir
RUN find $HADOOP_HOME/ -maxdepth 1 -not -name 'lib' ! -path $HADOOP_HOME/ -exec rm -rf {} \;

# hbase
ENV HBASE_TGZ_URL=https://mirrors.tuna.tsinghua.edu.cn/apache/hbase/stable/hbase-2.4.9-bin.tar.gz
ENV HBASE_HOME=/opt/hbase
ENV PATH=$HBASE_HOME/bin:$PATH
RUN set -ex; \
    mkdir -p $HBASE_HOME; \
    wget -nv -O $HBASE_HOME/src.tgz $HBASE_TGZ_URL; \
    tar -xf $HBASE_HOME/src.tgz --strip-components=1 -C $HBASE_HOME; \
    rm $HBASE_HOME/src.tgz; \
    chown -R root:root $HBASE_HOME;

RUN rm -rf $HBASE_HOME/docs/;

COPY docker-entrypoint.sh /
EXPOSE 22 9870 9000
ENTRYPOINT ["/docker-entrypoint.sh"]
