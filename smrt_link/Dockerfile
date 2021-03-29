FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="SMRT LINK v9.0"
LABEL description="Docker image for SMRT Link server"
USER root
WORKDIR /
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8
ENV LC_CTYPE en_US.UTF-8
ENV LC_MESSAGES en_US.UTF-8
RUN set -ex && \
    apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      apt-utils \
      locales \
      cmake \
      g++ \
      libxml2-dev \
      ca-certificates \
      zlib1g-dev \
      libfftw3-dev \
      unzip \
      wget \
      libssl-dev \
      openssl \
      rsync \
      curl \
      default-jre \
      net-tools \
      build-essential && \
    locale-gen "en_US.UTF-8" && \
    update-locale LANG=en_US.UTF-8 && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
ENV SMRT_USER smrt
RUN useradd -ms /bin/bash $SMRT_USER
USER $SMRT_USER
ENV SMRT_ROOT /home/smrt/smrtlink
RUN set -ex && \
    wget -q -O /tmp/smrtlink_9.0.0.92188.zip \
      https://downloads.pacbcloud.com/public/software/installers/smrtlink_9.0.0.92188.zip && \
    cd /tmp && \
    unzip smrtlink_9.0.0.92188.zip && \
    /tmp/smrtlink_9.0.0.92188.run --rootdir $SMRT_ROOT \
    --dnsname 0.0.0.0 \
    --batch \
    --skip-system-check \
    --skip-backup \
    --ignore-system-check && \
    rm -f /tmp/smrtlink_9.0.0.92188.*
EXPOSE 8243
EXPOSE 9090
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]