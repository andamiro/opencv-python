```python
import cv2

img = cv2.imread("lenna.bmp")

height, width = img.shape[:2]
center = (width / 2, height / 2)

while True:
    key = input("회전 각도 입력: ")

    if key == 'q':
        break

    angle = int(key)

    M = cv2.getRotationMatrix2D(center, angle, 1.0)

    img = cv2.warpAffine(img, M, (width, height))

    cv2.imshow("Repeated Rotation", img)
    cv2.waitKey(1)

cv2.destroyAllWindows()
```

회전 결과의 좌표가 정수가 아니기 떄문에 픽셀 위치를 정할 때 정수 좌표를 정해주는데 이부분에서 주변 픽셀값들이 회전시마다 조금씩 섞이게 된다.
