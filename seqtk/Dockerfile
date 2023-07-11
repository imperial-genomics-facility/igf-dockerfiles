FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="Seqtk_V1.4"
LABEL description="Docker image for Seqtk"
USER root
WORKDIR /
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      apt-utils \
      locales \
      cmake \
      g++ \
      wget \
      gzip \
      unzip \
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
    wget -O v1.4.tar.gz https://github.com/lh3/seqtk/archive/refs/tags/v1.4.tar.gz && \
    tar -xzf v1.4.tar.gz && \
    cd seqtk && \
    make && \
    mv seqtk /TOOLS/seqtk && \
    chmod a+x /TOOLS/seqtk && \
    rm -f /tmp/v1.4.tar.gz
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
ENV PATH=${PATH}:/TOOLS/
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]