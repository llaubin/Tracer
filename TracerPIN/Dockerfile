FROM debian:12.5

ENV PIN_ROOT /opt/pin-3.30-98830-g1d7b601b3-gcc-linux

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
    apt-get install -y  \
        wget curl make g++ gcc-multilib g++-multilib  && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN cd tmp && \
    curl -LOf http://software.intel.com/sites/landingpage/pintool/downloads/pin-3.30-98830-g1d7b601b3-gcc-linux.tar.gz && \
    tar xzf pin-3.30-98830-g1d7b601b3-gcc-linux.tar.gz && \
    mv pin-3.30-98830-g1d7b601b3-gcc-linux /opt && \
    rm pin-3.30-98830-g1d7b601b3-gcc-linux.tar.gz 

ADD . /root/tracer

RUN cd /root/tracer && \
    make && \
    make install && \
    make clean 

CMD ["bash"]
