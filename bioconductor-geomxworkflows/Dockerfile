FROM bioconductor/bioconductor_docker:3.17
RUN apt-get update && \
    R -e 'BiocManager::install("GeoMxWorkflows")' && \
    R -e 'BiocManager::install("GeomxTools")' && \
    R -e 'BiocManager::install("NanoStringNCTools")' && \
    R -e 'BiocManager::install("Seurat")'
RUN python3 -m pip install --upgrade pip setuptools wheel && \
    pip3 install --no-cache-dir jupyterlab setuptools rpy2 scanpy openpyxl altair
RUN R -e 'install.packages("IRkernel", repos="https://cloud.r-project.org/"); IRkernel::installspec();' && \
    R -e 'install.packages("remotes", repos="https://cloud.r-project.org/");' && \
    R -e 'remotes::install_github("mojaveazure/seurat-disk")' && \
    R -e 'devtools::install_github("satijalab/seurat-data")'
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*
RUN R -e 'IRkernel::installspec(user = FALSE)'
USER rstudio
WORKDIR /home/rstudio/work
ENV LD_LIBRARY_PATH /usr/local/lib/R/lib:/usr/local/lib:/usr/lib/x86_64-linux-gnu:/usr/lib/jvm/java-11-openjdk-amd64/lib/server
EXPOSE 8888
