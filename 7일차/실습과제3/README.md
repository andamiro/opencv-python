```python
import cv2

src = cv2.imread("lenna.bmp")

height, width = src.shape[:2]
center = (width / 2, height / 2)

while True:
    key = input("회전 각도 입력(q 입력 시 종료): ")

    if key == 'q':
        break

    angle = float(key)

    M = cv2.getRotationMatrix2D(center, angle, 1.0)

    dst = cv2.warpAffine(src, M, (width, height))

    cv2.imshow("Original", src)
    cv2.imshow("Rotated", dst)

    cv2.waitKey(1)

cv2.destroyAllWindows()
```
