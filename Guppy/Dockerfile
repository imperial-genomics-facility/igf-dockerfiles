FROM centos:centos7
LABEL version="v0.01"
LABEL description="Docker image for running de-multiplexing pipeline using BCLConvert tool"
USER root
WORKDIR /tmp
COPY ont-guppy-cpu-6.0.1-1.el7.x86_64.rpm /tmp/ont-guppy-cpu-6.0.1-1.el7.x86_64.rpm
RUN yum install -y \
      hdf5 \
      epel-release \
     /tmp/hdf5-1.8.12-13.el7.x86_64.rpm
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
