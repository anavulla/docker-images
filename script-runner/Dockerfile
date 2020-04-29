FROM ubuntu:20.04

LABEL maintainer="Ajay Kumar Navulla"

RUN apt-get update && \
apt-get install -y software-properties-common && \
apt-get install -y curl && \
apt-get install -y zip unzip && \
apt-get install -y wget && \
apt-get install -y python2.7 && \
apt-get install -y alien && \
apt-get install -y libaio1

RUN wget --quiet https://download.oracle.com/otn_software/linux/instantclient/19600/oracle-instantclient19.6-basic-19.6.0.0.0-1.x86_64.rpm
RUN wget --quiet https://download.oracle.com/otn_software/linux/instantclient/19600/oracle-instantclient19.6-sqlplus-19.6.0.0.0-1.x86_64.rpm
RUN wget --quiet https://download.oracle.com/otn_software/linux/instantclient/19600/oracle-instantclient19.6-devel-19.6.0.0.0-1.x86_64.rpm

RUN alien -i oracle-instantclient19.6-basic-19.6.0.0.0-1.x86_64.rpm && \
alien -i oracle-instantclient19.6-sqlplus-19.6.0.0.0-1.x86_64.rpm && \
alien -i oracle-instantclient19.6-devel-19.6.0.0.0-1.x86_64.rpm

RUN rm -Rf *.rpm cqlsh-6.8.tar.gz

RUN wget --quiet https://downloads.datastax.com/enterprise/cqlsh-6.8.tar.gz && \
tar -xzvf cqlsh-6.8.tar.gz -C /usr/share

RUN ln -s /usr/share/cqlsh-6.8.0/bin/cqlsh /usr/bin/cqlsh

RUN ldconfig

RUN mkdir -p /usr/src/app/scripts/sql && \
mkdir -p /usr/src/app/scripts/cassandra

WORKDIR /usr/src/app
