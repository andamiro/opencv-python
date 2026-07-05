```python
import cv2
import numpy as np

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)

sharp_kernel = np.array([
    [-1, -1, -1],
    [-1,  9, -1],
    [-1, -1, -1]
], dtype=np.float32)

blur_kernel = np.ones((3, 3), np.float32) / 9

blur_first = cv2.filter2D(img, -1, blur_kernel)
blur_then_sharp = cv2.filter2D(blur_first, -1, sharp_kernel)

sharp_first = cv2.filter2D(img, -1, sharp_kernel)
sharp_then_blur = cv2.filter2D(sharp_first, -1, blur_kernel)

cv2.imshow('img', img)

cv2.imshow('blur', blur_first)
cv2.imshow('blur -> sharp', blur_then_sharp)

cv2.imshow('sharp', sharp_first)
cv2.imshow('sharp -> blur', sharp_then_blur)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
