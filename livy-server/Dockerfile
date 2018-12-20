FROM ubuntu:18.04

# docker build -t brainlounge/livy-on-k8s-server:0.5.0-s2.4.0-h2.6 .

RUN apt update && apt install -y dnsutils tmux wget curl gnupg watch apt-transport-https unzip openjdk-8-jdk apt-utils

RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list
RUN apt update && apt install -y kubectl 

RUN wget -q http://archive.apache.org/dist/incubator/livy/0.5.0-incubating/livy-0.5.0-incubating-bin.zip
RUN unzip livy-0.5.0-incubating-bin.zip
RUN mkdir livy-0.5.0-incubating-bin/logs
COPY livy.conf /livy-0.5.0-incubating-bin/conf/
COPY log4j.properties /livy-0.5.0-incubating-bin/conf/
COPY spark-blacklist.conf /livy-0.5.0-incubating-bin/conf/
COPY spark.conf /livy-0.5.0-incubating-bin/conf/

RUN wget -q http://archive.apache.org/dist/spark/spark-2.4.0/spark-2.4.0-bin-hadoop2.6.tgz
RUN tar xvzf spark-2.4.0-bin-hadoop2.6.tgz 

ENV SPARK_HOME=/spark-2.4.0-bin-hadoop2.6
ENV SPARK_CONF=/livy-0.5.0-incubating-bin/conf/

EXPOSE 8998

COPY livy-server-on-k8s.sh /
ENTRYPOINT "/livy-server-on-k8s.sh"
