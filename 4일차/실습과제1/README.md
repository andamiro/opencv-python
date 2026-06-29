```python
import numpy as np
import cv2

img = np.zeros((400, 400, 3), np.uint8)
img2 = np.zeros((400, 400, 3), np.uint8)
img.fill(255)
img2.fill(255)

cv2.rectangle(img, (100, 100), (300, 300), 0, 1)
cv2.line(img, (100, 100), (300, 300), 0, 1)
cv2.line(img, (100, 300), (300, 100), 0, 1)

cv2.rectangle(img2, (100, 100), (300, 300), 0, 1)
cv2.circle(img2, (200, 200), 100, 0, 1)

cv2.imshow('src', img)
cv2.imshow('src2', img2)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
