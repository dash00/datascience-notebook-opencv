# datascience-notebook-opencv

This GitHub is associated with the following automated build on Dockerhub : [dash00/datascience-notebook-opencv](https://hub.docker.com/r/dash00/datascience-notebook-opencv/)

## Introduction:

Enjoy this very easy and very quick way to setup a full datascience environment! As you will see in the following sections, you will be able to install all popular libraries and packages to play with data with only one command line. 

## Why this project ? 

I had to setup a complete environment to practice image analysis based Machine Learning. I found very great ones but I was not able to find one which includes OpenCV which is very usefull to extract features from the images. Thus I decided to build my own ;) 

## How does it work ? 

The full datascience environment will be installed into a Docker container. Thus everything will be isolated and your system installation will not be impacted. When you run the container (as described below), a web service will be available and you will have an access through your web browser, that's it ! 

There are only three steps

1. install docker (if not already done)
2. run the container [dash00/datascience-notebook-opencv](https://hub.docker.com/r/dash00/datascience-notebook-opencv/)
3. access the IPython notebook web interface with your web browser and enjoy :)

### What does it include ? 

This container inherit from the excellent [jupyter/datascience-notebook docker](https://github.com/jupyter/docker-stacks/tree/master/datascience-notebook) image wich already includes 
- Jupyter Notebook 4.2.x
- Conda Python 3.x and Python 2.7.x environments
- pandas, matplotlib, scipy, seaborn, scikit-learn, scikit-image, sympy, cython, patsy, statsmodel, cloudpickle, dill, numba, bokeh pre-installed
- Conda R v3.2.x and channel
- plyr, devtools, dplyr, ggplot2, tidyr, shiny, rmarkdown, forecast, stringr, rsqlite, reshape2, nycflights13, caret, rcurl, and randomforest pre-installed
- Julia v0.3.x with Gadfly, RDatasets and HDF5 pre-installed

Here I simply add the following (based on the [izumin5210/notebook-dockerfiles](https://github.com/izumin5210/notebook-dockerfiles/blob/master/datascience-cv/Dockerfile) dockerfile) :

- cmake
- graphviz
- OpenCV 3.0

## Run a container : 

You can either rebuild the image with the attached Dockerfile or pull the last build of the image from DockerHub (most straightforward):

### Use the latest build from DockerHub

```
docker run -d -p 8888:8888 -v /$(pwd)/notebooks:/notebooks dash00/datascience-notebook-opencv
```
then add your notebooks into `/$(pwd)/notebooks` and got to the web interface at `localhost:8888` 

Options used : 
- `-d` run the container in background
- `-p <PORT>:8888` choose wich public port to expose, <PORT> should not be already in use. the service will be available at `localhost:<PORT>`
- `-v <SHARED>:/notebooks` share a folder with the container, <SHARED> will be created if it does not exist

### Build your own image from the Dockerfile

- Download the Dockerfile of this project.
- Build your image :
```
docker build -t my-own-datascience-notebook-opencv .
```
Option used : `-t` set the name of the image.

- Run the container 
```
docker run -d -p 8888:8888 -v /$(pwd)/notebooks:/notebooks my-own-datascience-notebook-opencv
```
(see previous subsection for more info on this command line)

## A test script : 

In order to test the correct installation of OpenCV, create a new notebook and copy, paste and run that code :

```python
%matplotlib inline
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('/notebooks/6683784.jpeg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img)
```
