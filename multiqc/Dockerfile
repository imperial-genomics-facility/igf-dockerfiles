FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="multiqc_v1.9"
LABEL description="Docker image for Multiqc tools"
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
      setuptools && \
    pip install \
      multiqc==1.9 && \
    rm -rf /var/lib/apt/lists/*
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
