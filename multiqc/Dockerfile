FROM python:3.9.16
LABEL maintainer="imperialgenomicsfacility"
LABEL version="multiqc_v1.14"
LABEL description="Docker image for Multiqc tools"
USER root
WORKDIR /
RUN apt-get -y update &&   \
    pip3 install --upgrade pip && \
    pip3 install multiqc==1.14 && \
    rm -rf /var/lib/apt/lists/*
USER nobody
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
