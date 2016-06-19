# datascience-notebook-opencv


## Run a container : 

```
docker run -d -p 8888:8888 -v /$(pwd)/notebooks:/notebooks dash00/datascience-notebook-opencv
```
then add your notebooks into `/$(pwd)/notebooks`

## A test script : 

```python
%matplotlib inline
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('/notebooks/6683784.jpeg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img)
```
