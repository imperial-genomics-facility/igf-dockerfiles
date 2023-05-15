FROM bioconductor/bioconductor_docker:3.17
RUN apt-get update && \
    R -e 'BiocManager::install("regionReport")' && \
    R -e 'BiocManager::install("DESeq2")' && \
    pip install jupyterlab && \
    R -e 'install.packages("IRkernel", repos="https://cloud.r-project.org/"); IRkernel::installspec();' && \
    apt-get clean && \
	rm -rf /var/lib/apt/lists/*
RUN R -e 'IRkernel::installspec(user = FALSE)'
EXPOSE 8888
