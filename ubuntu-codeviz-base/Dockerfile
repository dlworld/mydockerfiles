FROM ubuntu:14.04
MAINTAINER samuelololol <samuelololol@gmail.com>
COPY install_gcc-4.6.2.sh /root/
RUN apt-get update && \
    apt-get build-dep -y gcc-4.6-base && \
    apt-get install -y ncftp wget git && \
    cd /usr/include && ln -s x86_64-linux-gnu/* .; \
    cd /usr/lib && ln -s x86_64-linux-gnu/crt* .; \
    cd /root/ && git clone https://github.com/petersenna/codeviz.git && \
    cd /root/ && cp /root/install_gcc-4.6.2.sh /root/codeviz/compilers/install_gcc-4.6.2.sh && \
    cd /root/codeviz/ && ./configure && make && make install && \
    rm -rf /root/codeviz && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt-lists/*
