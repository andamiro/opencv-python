```python
import numpy as np
import cv2

image = cv2.imread("lenna.bmp", cv2.IMREAD_GRAYSCALE)
if image is None: raise Exception("파일읽기오류")

for r in range(image.shape[0]):
    for c in range(image.shape[1]):
        if image[r][c] >= 128: image[r][c] = min(255, image[r][c] * 1.2)
        else: image[r][c] *= 0.8

cv2.imshow("image", image)
cv2.waitKey(0)
```
