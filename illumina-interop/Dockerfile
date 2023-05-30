FROM python:3.9.16
LABEL maintainer="imperialgenomicsfacility"
LABEL version="Illumina-interop_v1.2.4"
LABEL description="Docker image for Illumina Interop tools"
USER root
ADD requirements_v1.2.4.txt /tmp/requirements.txt
RUN pip install --no-cache-dir -r /tmp/requirements.txt && \
    rm -f /tmp/requirements.txt
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]