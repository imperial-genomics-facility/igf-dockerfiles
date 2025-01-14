FROM python:3.10.15
LABEL maintainer="imperialgenomicsfacility"
LABEL version="bclconvert_reports:v5"
LABEL description="Docker image for BCLConvert reports"
USER root
ARG VERSION="1.3.2"
ARG PLATFORM="Linux-GNU"
WORKDIR /tmp
RUN wget -O /tmp/interop.tar.gz https://github.com/Illumina/interop/releases/download/v${VERSION}/interop-${VERSION}-${PLATFORM}.tar.gz && \
    tar -xzf interop.tar.gz && \
    mv interop-${VERSION}-${PLATFORM} interop && \
    mv /tmp/interop /opt && \
    rm -rf /tmp/*
RUN pip install numpy pandas iplotter jupyter nbconvert
RUN groupadd -g 1001 bclconvert && \
    useradd bclconvert -u 1001 -g 1001 && \
    mkdir -p /home/bclconvert
USER bclconvert
ENV PATH=${PATH}:/opt/interop/bin
VOLUME ["/data"]
ENV JUPYTER_PATH=/data
ENV JUPYTER_DATA_DIR=/data
ENV JUPYTER_RUNTIME_DIR=/data
WORKDIR /data
ENTRYPOINT ["/usr/local/bin/jupyter"]