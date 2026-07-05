```python
import cv2
import numpy as np

src = cv2.imread("scaling.jpg", cv2.IMREAD_GRAYSCALE)

height, width = src.shape[:2]

scale_x = 1.5
scale_y = 1.5

dst_height = int(height * scale_y)
dst_width = int(width * scale_x)

dst = np.zeros((dst_height, dst_width, 3), dtype=np.uint8)

for y in range(height):
    for x in range(width):
        new_x = int(x * scale_x)
        new_y = int(y * scale_y)

        if 0 <= new_x < dst_width and 0 <= new_y < dst_height:
            dst[new_y, new_x] = src[y, x]

cv2.imshow("src", src)
cv2.imshow("dst", dst)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
