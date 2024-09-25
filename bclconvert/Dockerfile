FROM centos:centos7.9.2009
LABEL version="v4.3.6"
LABEL description="Docker image for running de-multiplexing pipeline using BCLConvert tool v4.3.6"
USER root
WORKDIR /
COPY bcl-convert-4.3.6-2.el7.x86_64.rpm /tmp/bcl-convert.rpm
RUN sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/CentOS-*.repo
RUN cd /tmp && \
    yum install -y gcc gcc-c++ gdb && \
    rpm -i /tmp/bcl-convert.rpm && \
    rm -f /tmp/bcl-convert.rpm && \
    rm -rf /tmp/*
RUN groupadd -g 1001 bclconvert && \
    useradd bclconvert -u 1001 -g 1001
USER bclconvert
VOLUME ["/data"]
WORKDIR /data
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
