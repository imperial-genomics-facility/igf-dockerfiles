FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="HTSlib_Samtools_v1.11"
LABEL description="Docker image for HTSlib and Samtools"
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
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV PATH=${PATH}:/samtools/bin:/htslib/bin
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]