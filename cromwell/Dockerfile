FROM ubuntu:22.04
LABEL maintainer="imperialgenomicsfacility"
LABEL version="Cromwell_v86"
LABEL description="Docker image for Cormwell server"
USER root
WORKDIR /
WORKDIR /
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y wget openjdk-21-jre && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN mkdir /app && \
    wget -q -P /app https://github.com/broadinstitute/cromwell/releases/download/86/cromwell-86.jar
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh", "-c"]
CMD ["/bin/bash"]