ARG BASE_CONTAINER=adamjm32/kf-minimal-notebook
FROM $BASE_CONTAINER
ARG ARCH=amd64
LABEL maintainer="Adam Makarucha"

# Install kubernetes based cli's
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.11/bin/linux/$ARCH/kubectl && \ 
     chmod +x ./kubectl && mv ./kubectl /usr/local/bin/kubectl && \
     wget -c https://get.helm.sh/helm-v3.1.2-linux-$ARCH.tar.gz -O - | tar -xz -C /usr/local/bin/

# Install KF python libs  (using pip as these are not in the conda repos)
RUN eval "$(conda shell.bash hook |sed 's/base/wmlce/g')" && \
    pip install kfp \
    kubeflow-fairing



