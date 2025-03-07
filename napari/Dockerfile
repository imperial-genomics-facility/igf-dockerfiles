FROM ghcr.io/napari/napari:sha-f5de441
ENV QT_QPA_PLATFORM=offscreen
RUN apt install wget && \
    wget -O /tmp/napari_CosMx-0.4.17.3-py3-none-any.whl \
    "https://raw.githubusercontent.com/Nanostring-Biostats/CosMx-Analysis-Scratch-Space/refs/heads/Main/assets/napari-cosmx%20releases/napari_CosMx-0.4.17.3-py3-none-any.whl" && \
    pip3 install /tmp/napari_CosMx-0.4.17.3-py3-none-any.whl && \
    pip3 install --upgrade numba numpy==1.26.4
WORKDIR /tmp
ENTRYPOINT ["sh","-c"]
CMD ["/bin/bash"]