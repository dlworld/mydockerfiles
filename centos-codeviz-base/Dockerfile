FROM centos:7
MAINTAINER dlworld <denglinwen@gmail.com>
COPY install_gcc-4.6.2.sh /root/
RUN yum update -y && \
    yum install -y ftp wget git which make graphviz gcc g++ patch
RUN cd /root/ && wget ftp://ftp.gnu.org/pub/gnu/gcc/gcc-4.6.2/gcc-4.6.2.tar.gz && \
    tar xvf gcc-4.6.2.tar.gz && cd gcc-4.6.2 && \
    wget ftp://gcc.gnu.org/pub/gcc/infrastructure/mpfr-2.4.2.tar.bz2 && \
    tar xvf mpfr-2.4.2.tar.bz2 && ln -sf mpfr-2.4.2 mpfr && rm -rf mpfr-2.4.2.tar.bz2 && \
    wget ftp://gcc.gnu.org/pub/gcc/infrastructure/gmp-4.3.2.tar.bz2 && \
    tar xvf gmp-4.3.2.tar.bz2 && ln -sf gmp-4.3.2 gmp && rm -rf gmp-4.3.2.tar.bz2 && \
    wget ftp://gcc.gnu.org/pub/gcc/infrastructure/mpc-0.8.1.tar.gz && \
    tar xvf mpc-0.8.1.tar.gz && ln -sf mpc-0.8.1 mpc && rm -rf mpc-0.8.1.tar.gz && \
    tar czvf gcc-4.6.2.tar.gz gcc-4.6.2 && rm -rf gcc-4.6.2
RUN cd /usr/include && ln -s x86_64-linux-gnu/* .; \
    cd /usr/lib && ln -s x86_64-linux-gnu/crt* .; \
    cd /root/ && git clone https://github.com/petersenna/codeviz.git && \
    mv gcc-4.6.2.tar.gz /root/codeviz/compilers/ &&\
    cd /root/ && cp /root/install_gcc-4.6.2.sh /root/codeviz/compilers/install_gcc-4.6.2.sh && \
    cd /root/codeviz/ && ./configure && make && make install && \
    rm -rf /root/codeviz && \
    yum clean all

