```python
import cv2

image = cv2.imread("lenna.bmp")

height, width = image.shape[:2]

center = (width / 2, height / 2)

angle = -45
scale = 2.0

M = cv2.getRotationMatrix2D(center, angle, scale)

M[0, 2] += width / 2
M[1, 2] += height / 2

rotated_image = cv2.warpAffine(image, M, (width * 2, height * 2))

cv2.imshow('src', image)
cv2.imshow('dst', rotated_image)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
