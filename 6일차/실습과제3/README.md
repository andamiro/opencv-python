```python
import cv2
import numpy as np

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)

kernel = np.array([
    [-1, 0, 1],
    [-2, 0, 2],
    [-1, 0, 1]
], dtype=np.float32)

dst0 = cv2.filter2D(img, -1, kernel, delta=0)

dst128 = cv2.filter2D(img, -1, kernel, delta=128)

cv2.imshow('src', img)
cv2.imshow('delta 0', dst0)
cv2.imshow('delta 128', dst128)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
