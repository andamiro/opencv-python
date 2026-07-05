```python
import numpy as np
import cv2

image = cv2.imread("lenna.bmp")

height, width = image.shape[:2]

scale = 0.5

tx = width * (1 - scale) / 2
ty = height * (1 - scale) / 2

M = np.array([
    [scale, 0, tx],
    [0, scale, ty]
], dtype=np.float32)

dst = cv2.warpAffine(image, M, (width, height))

cv2.imshow('src', image)
cv2.imshow('dst', dst)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
