FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="FastqScreen_v0.15.0"
LABEL description="Docker image for FastqScreen"
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
      unzip \
      tar \
      ca-certificates \
      zlib1g-dev \
      libfftw3-dev \
      perl \
      libgd-perl \
      build-essential && \
    locale-gen en_US.UTF-8 && \
    dpkg-reconfigure locales && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN cd /tmp && \
    mkdir /fastq_screen && \
    wget -q -O /tmp/v0.15.0.tar.gz https://github.com/StevenWingett/FastQ-Screen/archive/refs/tags/v0.15.0.tar.gz && \
    tar -xzf /tmp/v0.15.0.tar.gz && \
    mv FastQ-Screen-0.15.0 /fastq_screen && \
    mkdir /bowtie2 && \
    wget -q -O /tmp/bowtie2-2.4.4-linux-x86_64.zip https://downloads.sourceforge.net/project/bowtie-bio/bowtie2/2.4.4/bowtie2-2.4.4-linux-x86_64.zip && \
    unzip bowtie2-2.4.4-linux-x86_64.zip && \
    mv bowtie2-2.4.4-linux-x86_64 /bowtie2 && \
    cd /tmp && \
    rm -f /tmp/v0.15.0.tar.gz /tmp/bowtie2-2.4.4-linux-x86_64.zip && \
    ln -s /bowtie2/bowtie2-2.4.4-linux-x86_64 /bowtie2/bin && \
    ln -s /fastq_screen/FastQ-Screen-0.15.0 /fastq_screen/bin
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV PATH=${PATH}:/bowtie2/bin:/fastq_screen/bin
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]