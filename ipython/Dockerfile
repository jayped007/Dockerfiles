FROM miniconda3
LABEL maintainer=@jayped007
RUN conda update conda && \
    conda install --quiet --yes ipython && \
    conda clean -tipsy
CMD ["ipython"]
