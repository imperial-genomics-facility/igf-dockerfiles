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
      openjdk-8-jre \
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
    wget -O fastqc_v0.11.9.zip https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.9.zip && \
    unzip fastqc_v0.11.9.zip && \
    mv FastQC /FastQC && \
    chmod a+x /FastQC/fastqc && \
    rm -f fastqc_v0.11.9.zip
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV PATH=${PATH}:/FastQC/
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
