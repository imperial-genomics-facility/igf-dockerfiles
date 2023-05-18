FROM python:3.9.16
LABEL maintainer="imperialgenomicsfacility"
LABEL version="scanpy_v1.9.3"
LABEL description="Docker image for scanpy tools"
USER root
ENV NB_USER notebook
ENV NB_GROUP notebook
ENV NB_UID 1000
RUN adduser --disabled-password \
      --gecos "Default user" \
      --uid ${NB_UID} \
      ${NB_USER} && \
    usermod -a -G $NB_GROUP $NB_USER
RUN apt-get -y update &&   \
    apt-get install --no-install-recommends -y \
      libfontconfig1 \
      libxrender1 \
      libreadline-dev \
      libreadline8 \
      libicu-dev \
      libc6-dev \
      icu-devtools \
      libjpeg-dev \
      libxext-dev \
      libcairo2 \
      libicu67 \
      libicu-dev \
      gcc \
      g++ \
      make \
      libgcc-9-dev \
      gfortran \
      git  && \
    apt-get purge -y --auto-remove && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN pip install --upgrade pip
ADD requirements.txt /data/requirements.txt
RUN pip install --no-cache-dir -r /data/requirements.txt
USER notebook
WORKDIR /home/notebook
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]