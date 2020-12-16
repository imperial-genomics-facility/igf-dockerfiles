FROM ubuntu:18.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="picard_2.23.9"
LABEL description="Docker image for Picard tools"
USER root
WORKDIR /
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      apt-transport-https \
      software-properties-common \
      gpg-agent \
      dirmngr && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9 && \
    add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran40/" && \
    apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      apt-utils \
      locales \
      cmake \
      g++ \
      wget \
      libxml2-dev \
      ca-certificates \
      zlib1g-dev \
      libfftw3-dev \
      build-essential \
      default-jre \
      openjdk-11-jre-headless \
      openjdk-8-jre-headless && \
    DEBIAN_FRONTEND="noninteractive"  TZ="Europe/London" apt-get install --no-install-recommends -y \
      tzdata \
      r-base && \
    locale-gen en_US.UTF-8 && \
    dpkg-reconfigure locales && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
#USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
WORKDIR /picard
RUN wget -O /picard/picard.jar \
  https://github.com/broadinstitute/picard/releases/download/2.23.9/picard.jar
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
