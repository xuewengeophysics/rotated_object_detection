

Make sure the labels format is [poly classname diffcult], e.g., You can set **diffcult=0**

```
  x1      y1       x2        y2       x3       y3       x4       y4       classname     diffcult

1686.0   1517.0   1695.0   1511.0   1711.0   1535.0   1700.0   1541.0   large-vehicle      1
```



https://github.com/Acid-knight/Annotations_Tool.git

使用上述工具将将rolabelImg格式(cx,cy,w,h,θ)转化为DOTA数据集的txt格式



```python
import numpy as np
import cv2
poly = np.array([240.0, 593.0, 206.0, 622.0, 191.0, 605.0, 225.0, 576.0])
poly = np.float32(poly.reshape(4, 2))
(x, y), (w, h), angle = cv2.minAreaRect(poly)
```



**[DOTA数据格式转YOLO数据格式工具(cv2.minAreaRect踩坑记录)](https://zhuanlan.zhihu.com/p/356416158)**:

**4.5版本以上的opencv cv2.minAreaRect()函数生成的θ范围已经不是∈[-90, 0)**

```python
# opencv-python 4.1.2.30
-40.46222686767578
# opencv-python 4.6.0.66
49.53777313232422
```



```
train_path
```



