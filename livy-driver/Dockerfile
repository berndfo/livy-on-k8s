FROM brainlounge/spark:2.4.0-hadoop-2.6

# docker build -t brainlounge/livy-on-k8s-driver:livy-0.5.0-s2.4.0-h2.6 .

RUN apk add unzip
ADD http://archive.apache.org/dist/incubator/livy/0.5.0-incubating/livy-0.5.0-incubating-bin.zip livy-0.5.0-incubating-bin.zip
RUN unzip livy-0.5.0-incubating-bin.zip
