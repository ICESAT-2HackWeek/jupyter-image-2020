# jupyter-image-2020
Repository for builing Icesat2 Hackweek 2020 [JupyterHub](https://jupyter.org/hub) environment with [Repo2Docker](https://repo2docker.readthedocs.io/en/latest/) and [GitHub Actions CI](https://help.github.com/en/actions/automating-your-workflow-with-github-actions)

![Action Status](https://github.com/ICESAT-2HackWeek/jupyter-image-2020/workflows/Repo2Docker/badge.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/uwhackweeks/icesat2)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ICESAT-2HackWeek/jupyter-image-2020/master?urlpath=lab)

### How to use
* fork this repository and make a PR to change image configuration in binder/ repository

* commits to master branch trigger re-building image tagged by github short sha and 'latest'
```
git commit -a -m "modified binder/environment to my liking"
git push
```
* pushing a tag results in a docker image with the same tag:
```
git tag -am "tagging 2020" 2020
git push --tags
```

### Pull DockerHub image to run a local JupyterLab session
https://hub.docker.com/repository/docker/uwhackweeks/icesat2
```
export IMAGE=uwhackweeks/icesat2
export TAG=latest
docker pull docker.pkg.github.com/$IMAGE:$TAG
docker run -it --name repo2docker -p 8888:8888 $IMAGE:$TAG jupyter lab --ip 0.0.0.0
docker stop repo2docker
docker rm repo2docker
```
