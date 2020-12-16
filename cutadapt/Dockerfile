FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="cutadapt_v3.1"
LABEL description="Docker image for Cutadapt tools"
USER root
WORKDIR /
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      apt-utils \
      locales \
      cmake \
      g++ \
      libxml2-dev \
      ca-certificates \
      zlib1g-dev \
      libfftw3-dev \
      build-essential \
      python3 \
      python3-pip && \
    locale-gen en_US.UTF-8 && \
    dpkg-reconfigure locales && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    pip3 install --upgrade pip && \
    pip install \
      setuptools \
      cutadapt==3.1 && \
    rm -rf /var/lib/apt/lists/*
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
