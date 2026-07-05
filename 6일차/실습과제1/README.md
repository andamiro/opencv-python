```python
import cv2
import numpy as np

img = cv2.imread('rose.bmp', cv2.IMREAD_GRAYSCALE)
noise = np.random.normal(0, 20, img.shape)
noise_img = img + noise
noise_img = np.clip(noise_img, 0, 255).astype(np.uint8)

kernel = np.ones((5, 5), np.float32) / 25
blur = cv2.filter2D(img, -1, kernel)

cv2.imshow('src', img)
cv2.imshow('noise', noise_img)
cv2.imshow('blur', blur)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
