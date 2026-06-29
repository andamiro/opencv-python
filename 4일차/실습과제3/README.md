```python
import numpy as np
import cv2

img = np.zeros((400, 1200, 3), np.uint8)

img1 = img[:400, :400]
img1[:] = (255, 0, 0)
cv2.rectangle(img1, (100, 100), (300, 300), (255, 255, 255), 10)

img2 = img[:400, 400:800]
img2[:] = (0, 255, 0)
cv2.circle(img2, (200, 200), 100, (255, 255, 255), 10)

img3 = img[:400, 800:1200]
img3[:] = (0, 0, 255)
cv2.line(img3, (100, 100), (300, 300), (255, 255, 255), 10)
cv2.line(img3, (300, 100), (100, 300), (255, 255, 255), 10)

cv2.imshow('src', img)
cv2.waitKey(0)

cv2.destroyAllWindows()
```
