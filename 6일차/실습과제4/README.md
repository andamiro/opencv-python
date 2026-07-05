```python
import numpy as np
import cv2

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)

spos = (0, 0)
result = img.copy()

kernel = np.ones((15, 15), np.float32) / (15 * 15)

def on_mouse(event, x, y, flags, param):
    global spos, result

    if event == cv2.EVENT_LBUTTONDOWN:
        spos = (x, y)

    elif event == cv2.EVENT_LBUTTONUP:
        min_x = min(spos[0], x)
        min_y = min(spos[1], y)
        max_x = max(spos[0], x)
        max_y = max(spos[1], y)

        if min_x == max_x or min_y == max_y:
            return

        select = result[min_y:max_y, min_x:max_x]
        blur_select = cv2.filter2D(select, -1, kernel)
        result[min_y:max_y, min_x:max_x] = blur_select

        cv2.imshow('blur', result)

cv2.imshow('blur', result)
cv2.setMouseCallback('blur', on_mouse)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
