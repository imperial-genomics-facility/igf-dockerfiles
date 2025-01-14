FROM quay.io/biocontainers/star:2.6.1d--0
LABEL version="v2.6.1d"
LABEL description="Docker image for running STAR v2.6.1d"
USER root
WORKDIR /tmp
RUN wget https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -O /tmp/awscliv2.zip && \
    unzip awscliv2.zip && \
   ./aws/install && \
   rm -rf /tmp/*
VOLUME ["/data"]