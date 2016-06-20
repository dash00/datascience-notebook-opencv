# datascience-notebook-opencv

With this project it becomes very easy and fast to install a full datascience environment : 

1. install docker
2. run the container dash00/datascience-notebook-opencv
3. enjoy :)

This GitHub is associated with the following automated build on Dockerhub : [dash00/datascience-notebook-opencv](https://hub.docker.com/r/dash00/datascience-notebook-opencv/)

You can either rebuild the image with the attached Dockerfile or pull the last build of the image from DockerHub (see Run a container below).

## Run a container : 

```
docker run -d -p 8888:8888 -v /$(pwd)/notebooks:/notebooks dash00/datascience-notebook-opencv
```
then add your notebooks into `/$(pwd)/notebooks` and got to the web interface at `localhost:8888` 

Options used : 
- `-d` run the container in background
- `-p <PORT>:8888` choose wich public port to expose, <PORT> should not be already in use. the service will be available at `localhost:<PORT>`
- `-v <SHARED>:/notebooks` share a folder with the container, <SHARED> will be created if it does not exist

## A test script : 

Create a new notebook and copy, paste and run that code :

```python
%matplotlib inline
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('/notebooks/6683784.jpeg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img)
```
