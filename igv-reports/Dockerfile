FROM python:3.9.16
LABEL maintainer="imperialgenomicsfacility"
LABEL version="igv_reports_v1.7.0"
LABEL description="Docker image for IGV reports tools"
USER root
RUN pip install igv-reports==1.7.0 && \
    pysam==0.21.0 && \
    jupyterlab==3.6.3
USER nobody
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]