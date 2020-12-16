FROM centos:latest
LABEL version="v0.01"
LABEL description="Docker image for running de-multiplexing pipeline"
USER root
WORKDIR /
COPY bcl2fastq2-v2.20.0.422-Linux-x86_64.rpm /tmp/bcl2fastq2-v2.20.0.422-Linux-x86_64.rpm
RUN yum install -y /tmp/bcl2fastq2-v2.20.0.422-Linux-x86_64.rpm && \
    rm -f /tmp/bcl2fastq2-v2.20.0.422-Linux-x86_64.rpm && \
    rm -rf /tmp/*
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
