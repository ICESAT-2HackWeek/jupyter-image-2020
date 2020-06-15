# jupyter-image-2020
Repository for building Icesat2 Hackweek 2020 [JupyterHub](https://jupyter.org/hub) environment (Docker Image) with [GitHub Actions CI](https://help.github.com/en/actions/automating-your-workflow-with-github-actions)

![Action Status](https://github.com/ICESAT-2HackWeek/jupyter-image-2020/workflows/MasterBuild/badge.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/uwhackweeks/icesat2)
[![badge](https://img.shields.io/static/v1.svg?logo=Jupyter&label=Pangeo+Binder&message=AWS+us-west-2&color=orange)](https://staging.aws-uswest2-binder.pangeo.io/v2/gh/ICESAT-2HackWeek/jupyter-image-2020/master?urlpath=git-pull?repo=https://github.com/ICESAT-2HackWeek/ICESat2_hackweek_tutorials%26amp%3Bbranch=master%26amp%3Burlpath=lab%3Fautodecode)



This repository contains configuration for the standard environment used during the Icesat2 2020 Hackweek. When you log into the Icesat2 JupyterHub you are running a virtual machine with Ubuntu 18.04, a variety of command line tools like `vim` and `git`, a `conda` Python environment with compatibly package versions, and JupyterLab extensions such as `ipywidgets` and `ipyleaflet`. By packaging everything up with Docker we help ensure that code written during the hackweek is reproducible and can be run on different physical hardware today and in the future.


### Local Docker Installation
If you'd like to run exactly the same environment on your local machine you must have [Docker](https://docs.docker.com/get-docker/) installed on your computer. Running the following command from a terminal will launch JupyterLab in your browser:

```
docker run -it -v $PWD:/home/jovyan --rm -p 8888:8888 uwhackweeks/icesat2:2020.06.15 jupyter lab --ip 0.0.0.0
```

Consult the [Docker documentation](https://docs.docker.com/engine/reference/run/) for details on the `docker run` command. The key thing to note is that we're using the same Docker image used during the hackweek (`uwhackweeks/icesat2:2020.06.15`). And you map the current directory to your jupyter home folder with `-v $PWD:/home/jovyan`.


### Local conda environment
You might be interested in installing just the Python [conda environment](https://icesat-2hackweek.github.io/learning-resources/preliminary/conda/) from the 2020 hackweek. We provide a lock file so that you can install **exactly the same packages** on Linux:
```
conda create -n icesat2020 --file=https://raw.githubusercontent.com/ICESAT-2HackWeek/jupyter-image-2020/2020.06.15/conda-linux-64.lock
```

For Linux, MacOSX, or Windows, if you're not concerned with package versions and simply want to have the same libraries installed on your system you can run:
```
conda env create --file=https://raw.githubusercontent.com/ICESAT-2HackWeek/jupyter-image-2020/2020.06.15/environment.yml
```

Note that you may have to comment out certain packages from the `environment.yml` if they are not available for your particular operating system.

Once you have installed the conda environment, you can install JupyterLab extensions with:
```
conda activate icesat2020
jupyter labextension install --clean @jupyter-widgets/jupyterlab-manager \
                                      @jupyterlab/server-proxy \
                                      @jupyterlab/geojson-extension \
                                      @pyviz/jupyterlab_pyviz \
                                      jupyter-matplotlib \
                                      jupyter-leaflet \
                                      dask-labextension
```

We also installed a few packages not on conda-forge, which are in a pip `requirements.txt`
```
pip install -r requirements.txt
```


Now you are ready to run `jupyter lab` to work with various notebooks and projects in the same environment on your local computer :tada:


### Additional resources

* Software Carpentry reference for setting up various tools like git and conda: https://uwescience.github.io/2020-05-11-uw-online/#setup
