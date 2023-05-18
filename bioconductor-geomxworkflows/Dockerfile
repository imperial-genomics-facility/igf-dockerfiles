FROM bioconductor/bioconductor_docker:3.17
RUN apt-get update && \
    R -e 'BiocManager::install("GeoMxWorkflows")' && \
    R -e 'BiocManager::install("GeomxTools")' && \
    R -e 'BiocManager::install("NanoStringNCTools")' && \
    pip install jupyterlab && \
    R -e 'install.packages("IRkernel", repos="https://cloud.r-project.org/"); IRkernel::installspec();' && \
    apt-get clean && \
	rm -rf /var/lib/apt/lists/*
RUN R -e 'IRkernel::installspec(user = FALSE)'
EXPOSE 8888