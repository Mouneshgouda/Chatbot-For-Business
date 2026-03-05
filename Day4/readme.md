## Anomaly Detection


```
!pip install --upgrade numpy matplotlib --force-reinstall

import numpy as np
import matplotlib.pyplot as plt
data = np.random.normal(0, 1, 20)          # normal data
threshold = 2                               # simple rule: >2 is anomaly
plt.scatter(range(len(data)), data, c=(abs(data)>threshold), s=100)  # color anomalies
plt.show()

```

## Computer vision
```

!nvidia-smi

```

```python
import os
HOME = os.getcwd()
print(HOME)

```


```python
# Pip install method (recommended)

!pip install ultralytics==8.2.103 -q

from IPython import display
display.clear_output()

# prevent ultralytics from tracking your activity
!yolo settings sync=False

import ultralytics
ultralytics.checks()
```

```
from ultralytics import YOLO

from IPython.display import display, Image

```

```python

%cd {HOME}
!yolo task=detect mode=predict model=yolov8n.pt conf=0.25 source='/content/WhatsApp Image 2026-02-05 at 7.33.11 PM.jpeg' save=True

```


```

%cd {HOME}
Image(filename='/content/runs/detect/predict/WhatsApp Image 2026-02-05 at 7.33.11 PM.jpeg', height=600)

```
