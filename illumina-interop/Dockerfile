FROM python:3.10
LABEL maintainer="imperialgenomicsfacility"
LABEL version="Illumina-interop_v1.2.4"
LABEL description="Docker image for Illumina Interop tools"
USER root
ENV NB_USER notebook
ENV NB_GROUP notebook
ENV NB_UID 1000
RUN adduser --disabled-password \
      --gecos "Default user" \
      --uid ${NB_UID} \
      ${NB_USER} && \
    usermod -a -G $NB_GROUP $NB_USER
WORKDIR /
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
        ca-certificates-java \
        openjdk-17-jre  && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN wget -O /tmp/interop-1.2.4-Linux-GNU.tar.gz \
    https://github.com/Illumina/interop/releases/download/v1.2.4/interop-1.2.4-Linux-GNU.tar.gz && \
    cd /tmp && \
    tar -xzf /tmp/interop-1.2.4-Linux-GNU.tar.gz && \
    cp -r interop-1.2.4-Linux-GNU/bin/* /usr/local/bin/ && \
    rm -rf interop-1.2.4-Linux-GNU*
RUN pip install --upgrade pip
ADD requirements_v1.2.4.txt /tmp/requirements.txt
RUN pip install --no-cache-dir -r /tmp/requirements.txt && \
    rm -f /tmp/requirements.txt
USER notebook
WORKDIR /home/notebook
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]