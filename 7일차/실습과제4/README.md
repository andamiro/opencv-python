```python
import cv2

src = cv2.imread("lenna.bmp")

height, width = src.shape[:2]
center = (width / 2, height / 2)

angle = 0

cv2.imshow("src", src)

while True:
    key = cv2.waitKey(0)

    if key == ord('q'):
        break

    elif key == ord('r'):
        angle -= 10

    elif key == ord('b'):
        angle += 10

    angle %= 360

    M = cv2.getRotationMatrix2D(center, angle, 1.0)

    dst = cv2.warpAffine(src, M, (width, height))

    cv2.imshow("src", dst)

cv2.destroyAllWindows()
```
