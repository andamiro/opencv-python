```python
import cv2
import os

cam = cv2.VideoCapture(0)
if not cam.isOpened(): raise Exception('can not find camera')

width = int(cam.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cam.get(cv2.CAP_PROP_FRAME_HEIGHT))

fps = 10
delay = round(1000 / fps)
size = (width, height)
fourcc = cv2.VideoWriter.fourcc(*'mp4v')

isRecording = False
writer = None

while True:
    ret, frame = cam.read()
    key = cv2.waitKey(delay)

    if isRecording:
        writer.write(frame)

    if key == ord('q'):
        if isRecording: writer.release()
        break
    elif key == ord('e'):
        if isRecording:
            isRecording = False
            writer.release()
            filename = input('filename: ')
            os.rename('temp.mp4', filename)
    elif key == ord('s'):
        if not isRecording:
            isRecording = True
            writer = cv2.VideoWriter('temp.mp4', fourcc, fps, size)
            if not writer.isOpened(): raise Exception('can not open video')

    cv2.imshow('cam', frame)

cam.release()
cv2.destroyAllWindows()
```
