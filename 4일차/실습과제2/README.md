```python
import numpy as np
import cv2

img = cv2.imread('lenna.bmp', cv2.IMREAD_COLOR_BGR)

blockSz = (img.shape[1] // 4, img.shape[0] // 4)

for i in range(4) :
    cv2.line(img, (blockSz[0] * i, 0), (blockSz[0] * i, img.shape[0]), (255, 255, 255), 1)
    cv2.line(img, (0, blockSz[0] * i), (img.shape[1], blockSz[0] * i), (255, 255, 255), 1)

cv2.imshow('src', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
