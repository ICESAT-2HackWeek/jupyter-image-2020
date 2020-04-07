# jupyter-image-2020
Repository for builing Icesat2 Hackweek 2020 [JupyterHub](https://jupyter.org/hub) environment with [Repo2Docker](https://repo2docker.readthedocs.io/en/latest/) and [GitHub Actions CI](https://help.github.com/en/actions/automating-your-workflow-with-github-actions)

![Action Status](https://github.com/ICESAT-2HackWeek/jupyter-image-2020/workflows/MasterBuild/badge.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/uwhackweeks/icesat2)
[![badge](https://img.shields.io/static/v1.svg?logo=Jupyter&label=Pangeo+Binder&message=AWS+us-west-2&color=orange)](https://staging.aws-uswest2-binder.pangeo.io/v2/gh/ICESAT-2HackWeek/jupyter-image-2020/binder?urlpath=git-pull?repo=https://github.com/ICESAT-2HackWeek/ICESat2_hackweek_tutorials%26amp%3Bbranch=master%26amp%3Burlpath=lab%3Fautodecode)

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
docker run -it --rm -p 8888:8888 uwhackweeks/icesat2:latest jupyter lab --ip 0.0.0.0
```
