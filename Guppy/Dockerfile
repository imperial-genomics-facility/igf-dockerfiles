FROM centos:centos7
LABEL version="v0.01"
LABEL description="Docker image for running de-multiplexing pipeline using BCLConvert tool"
USER root
WORKDIR /
COPY ont-guppy-cpu-6.0.1-1.el7.x86_64.rpm /home/ndawson/guppy_trial/ont-guppy-cpu-6.0.1-1.el7.x86_64.rpm
RUN cd /tmp && \
    yum install \
    yum insatall hdf5 \
    yum install epel-release \
#   /home/ndawson/guppy_trial/hdf5-1.8.12-13.el7.x86_64.rpm \
    yum install /home/ndawson/guppy_trial/zeromq-4.1.4-6.el7.x86_64.rpm \
    yum install /home/ndawson/guppy_trial/ont-guppy-cpu-6.0.1-1.el7.x86_64.rpm
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]
