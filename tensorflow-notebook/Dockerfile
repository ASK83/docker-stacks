# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/scipy-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Jupyter Project <jupyter@googlegroups.com>"

# Install Tensorflow
RUN conda install --quiet --yes \
    'tensorflow=1.13*' \
    'keras=2.2*' \
    'flask=1.0*' \
    'graphviz=2.38*' \
    'intel-openmp=2019.1*' \
    'libxgboost=0.90*' \
    'numpy=1.17*' \
    'parquet-cpp=1.5*' \
    'pyarrow=0.14*' \
    'colorama=0.4*' \
    'dask-glm=0.2*' \
    'dask-ml=1.0*' \
    'memory_profiler=0.55*' \
    'tpot=0.9*' \
    'turbodbc=3.2*' \
    'urllib3=1.25*' \
    'plotly=4.1*' \
    'scikit-plot=0.3*' \
    'imbalanced-learn=0.5*' && \
    conda clean --all -f -y && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

RUN conda install -c districtdatalabs --quiet --yes \
    'yellowbrick=1.*'

RUN git clone --recursive https://github.com/dmlc/xgboost && \
    cd xgboost && \
    make -j4 && \
    cd python-package; python setup.py install