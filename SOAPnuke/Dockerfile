FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="SOAPnuke v2.1.9"
LABEL description="Docker image for SOAPnuke"
USER root
WORKDIR /
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      apt-utils \
      locales \
      cmake \
      g++ \
      libxml2-dev \
      wget \
      bzip2 \
      libbz2-dev \
      liblzma-dev \
      libncurses5-dev \
      gzip \
      tar \
      ca-certificates \
      zlib1g-dev \
      libfftw3-dev \
      build-essential && \
    locale-gen en_US.UTF-8 && \
    dpkg-reconfigure locales && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN cd /tmp && \
    mkdir /samtools && \
    mkdir /htslib && \
    wget -q -O /tmp/htslib-1.11.tar.bz2 https://github.com/samtools/htslib/releases/download/1.11/htslib-1.11.tar.bz2 && \
    tar -xf /tmp/htslib-1.11.tar.bz2 && \
    cd htslib-1.11 && \
    ./configure --prefix=/htslib && \
    make && \
    make install && \
    cd /tmp && \
    wget -q -O /tmp/samtools-1.11.tar.bz2 https://github.com/samtools/samtools/releases/download/1.11/samtools-1.11.tar.bz2 && \
    tar -xf /tmp/samtools-1.11.tar.bz2 && \
    cd samtools-1.11 && \
    ./configure --prefix=/samtools && \
    make && \
    make install && \
    cd /tmp && \
    rm -f /tmp/htslib-1.11.tar.bz2 /tmp/samtools-1.11.tar.bz2
RUN cd /tmp && \
    wget -q -O /soapnuke/SOAPnuke-v2.1.9.tar.gz \
    https://github.com/BGI-flexlab/SOAPnuke/archive/refs/tags/SOAPnuke2.1.9.tar.gz && \
    tar -xf /soapnuke/SOAPnuke-v2.1.9.tar.gz && \
    cd SOAPnuke-SOAPnuke2.1.9 && \
    make && \
    cp -r /tmp/SOAPnuke-SOAPnuke2.1.9 /soapnuke
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV PATH=${PATH}:/samtools/bin:/htslib/bin:/soapnuke
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]