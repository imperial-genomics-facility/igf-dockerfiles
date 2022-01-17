FROM centos:centos7
LABEL version="v0.01"
LABEL description="Docker image for running de-multiplexing pipeline using BCLConvert tool"
USER root
WORKDIR /
COPY bcl-convert-3.9.3-2.el7.x86_64.rpm /tmp/bcl-convert-3.9.3-2.el7.x86_64.rpm
RUN cd /tmp && \
    yum install -y gcc gcc-c++ gdb && \
    rpm -i  bcl-convert-3.9.3-2.el7.x86_64.rpm && \
    rm -f /tmp/bcl-convert-3.9.3-2.el7.x86_64.rpm && \
    rm -rf /tmp/*
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]