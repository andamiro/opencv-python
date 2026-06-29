```python
import cv2
import numpy as np

img = np.zeros((500, 500, 3))
img.fill(255)

title = 'src'
bar_name = 'color'

color = 1
isClk = False
prev_cursor = (0, 0)

def getColor():
    global color
    if color == 0:
        return (255, 0, 0)
    elif color == 1:
        return (0, 255, 0)
    elif color == 2:
        return (0, 0, 255)

def onChange(value):
    global color
    color = value

def onMouse(event, x, y, flags, param):
    global img, color, title, isClk, prev_cursor
    if event == cv2.EVENT_LBUTTONDOWN:
        if not isClk:
            prev_cursor = (x, y)
            isClk = True
    elif event == cv2.EVENT_LBUTTONUP:
        isClk = False
    elif event == cv2.EVENT_MOUSEMOVE:
        if isClk:
            cv2.line(img, prev_cursor, (x, y), getColor(), 2)
            prev_cursor = (x, y)
    cv2.imshow(title, img)

cv2.imshow(title, img)
cv2.createTrackbar(bar_name, title, 0, 2, onChange)
cv2.setMouseCallback(title, onMouse)

while True: 
    if cv2.waitKey(1) == 27: break
    
cv2.destroyAllWindows()
```
