## kf-jupyter-docker-stacks/gpu-notebook  

[Source on GitLab](https://git.puma.corp.telstra.com/tail/notebook-images/kf-jupyter-docker-stacks/tree/master/gpu-notebook) | [Dockerfile commit history](https://git.puma.corp.telstra.com/tail/notebook-images/kf-jupyter-docker-stacks/commits/master/gpu-notebook/Dockerfile)

`kf-jupyter-docker-stacks/gpu-notebook` is a small gpu-enabled image supporting common options across all stacks and is the basis for all other gpu-enabled stacks.  This image supports `x86_64`/`amd64` and `ppc64le` processor architectures.

* Minimally functional Jupyter Notebook server (e.g. no Pandoc for saving notebooks as PDF's)
* Miniconda Python 3.7 installed to /opt/conda
* No scientific computing packages
* Unprivileged user `jovyan (uid=1000)` and group `users (gid=100)` with ownership of `/home/jovyan` and `/opt/conda` paths
* `tini` container entrypoint and `start-notebook.sh` script as default command
* passwordless sudo
* CUDA <version>
