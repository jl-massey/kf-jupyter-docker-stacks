# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=adamjm32/kf-kubeflow-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Adam Makarucha"

# ffmpeg for matplotlib anim & dvipng for latex labels
RUN apt-get update && \
    apt-get install -y --no-install-recommends ffmpeg dvipng && \
    rm -rf /var/lib/apt/lists/*

# Install Python 3 packages
RUN eval "$(conda shell.bash hook |sed 's/base/wmlce/g')" && \
    conda install --quiet --yes -n wmlce \
    "openblas" \
    'beautifulsoup4' \
    'openblas' \
    'bokeh' \
    'cloudpickle' \
    'cython' \
    'dask' \
    'dill' \
    'h5py' \
    'hdf5' \
    'ipywidgets' \
    'ipympl'\
    'matplotlib-base' \
    'numba' \
    'numexpr' \
    'pandas' \
    'patsy' \
    'protobuf' \
    'scikit-image' \
    'scikit-learn' \
    'scipy' \
    'seaborn' \
    'sqlalchemy' \
    'statsmodels' \
    'sympy' \
    'vincent' \
    'widgetsnbextension'\
    'xlrd' \
    && \
    conda clean --all -f -y && \
    # Activate ipywidgets extension in the environment that runs the notebook server
    jupyter nbextension enable --py widgetsnbextension --sys-prefix && \
    # Also activate ipywidgets extension for JupyterLab
    # Check this URL for most recent compatibilities
    # https://github.com/jupyter-widgets/ipywidgets/tree/master/packages/jupyterlab-manager
    jupyter labextension install @jupyter-widgets/jupyterlab-manager@^2.0.0 --no-build && \
    jupyter labextension install @bokeh/jupyter_bokeh@^2.0.0 --no-build && \
    jupyter labextension install jupyter-matplotlib@^0.7.2 --no-build && \
    jupyter lab build && \
    jupyter lab clean && \
    npm cache clean --force && \
    rm -rf /home/root/.cache/yarn && \
    rm -rf /home/root/.node-gyp

# Install facets which does not have a pip or conda package at the moment
RUN eval "$(conda shell.bash hook |sed 's/base/wmlce/g')" && cd /tmp && \
    git clone https://github.com/PAIR-code/facets.git && \
    cd facets && \
    jupyter nbextension install facets-dist/ --sys-prefix && \
    cd && \
    rm -rf /tmp/facets

# Import matplotlib the first time to build the font cache.
ENV XDG_CACHE_HOME /home/root/.cache/
RUN eval "$(conda shell.bash hook |sed 's/base/wmlce/g')" && MPLBACKEND=Agg python -c "import matplotlib.pyplot" 
