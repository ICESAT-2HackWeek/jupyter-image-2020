# jupyter-image-2020
Repository for building Icesat2 Hackweek 2020 [JupyterHub](https://jupyter.org/hub) environment (Docker Image) with [GitHub Actions CI](https://help.github.com/en/actions/automating-your-workflow-with-github-actions)

![Action Status](https://github.com/ICESAT-2HackWeek/jupyter-image-2020/workflows/MasterBuild/badge.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/uwhackweeks/icesat2)
[![badge](https://img.shields.io/static/v1.svg?logo=Jupyter&label=Pangeo+Binder&message=AWS+us-west-2&color=orange)](https://staging.aws-uswest2-binder.pangeo.io/v2/gh/ICESAT-2HackWeek/jupyter-image-2020/master?urlpath=git-pull?repo=https://github.com/ICESAT-2HackWeek/ICESat2_hackweek_tutorials%26amp%3Bbranch=master%26amp%3Burlpath=lab%3Fautodecode)

### How to make changes to the image
* fork this repository and make a PR to change any of the [image configuration files](https://mybinder.readthedocs.io/en/latest/config_files.html). Merging into the master branch or creating tags will automatically build and push new images to DockerHub (https://hub.docker.com/repository/docker/uwhackweeks/icesat2).

### How to run on your local computer
You must have [Docker](https://docs.docker.com/get-docker/) installed on your computer. Running the following command from a terminal will launch Jupyter Lab and link your current directory for reading and writing files.
```
docker run -it -v $PWD:/home/jovyan --rm -p 8888:8888 uwhackweeks/icesat2:master jupyter lab --ip 0.0.0.0
```
