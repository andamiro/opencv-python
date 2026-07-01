```python
import cv2
import numpy as np

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)

def onChange(value):
    cv2.imshow('dst', cv2.add(img, value))

cv2.imshow('dst', img)
cv2.createTrackbar('Brightness', 'dst', 0, 100, onChange)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
