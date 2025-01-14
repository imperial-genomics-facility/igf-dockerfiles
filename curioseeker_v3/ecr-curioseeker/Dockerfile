FROM curiobioinformatics/curio-seeker-pipeline:v3.0.0
LABEL version="v3.0.0"
LABEL description="Docker image for running curio-seeker pipeline v3.0.0"
USER root
RUN apt-get update && \
    apt-get install -y curl unzip && \
    rm -rf /tmp/*
RUN groupadd -g 1001 curio && \
    useradd curio -u 1001 -g 1001
WORKDIR /tmp
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
   ./aws/install && \
   rm -rf /tmp/*
USER curio
VOLUME ["/data"]