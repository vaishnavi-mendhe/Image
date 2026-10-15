## 20 Basic Image Processing Programs

Python + OpenCV • Exam revision codes

Before running: Install with pip install opencv-python matplotlib numpy. Keep image.jpg in the same folder as the program. Question 19 also needs image2.jpg.

## 1. Image Grayscale

```
import cv2
img = cv2.imread("image.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
cv2.imshow("Original", img)
cv2.imshow("Grayscale", gray)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 2. Image Resizing

```
import cv2
img = cv2.imread("image.jpg")
resized = cv2.resize(img, (300, 200))
cv2.imshow("Original", img)
cv2.imshow("Resized", resized)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 3. Image Rotation

```
import cv2
img = cv2.imread("image.jpg")
r90 = cv2.rotate(img, cv2.ROTATE_90_CLOCKWISE)
r180 = cv2.rotate(img, cv2.ROTATE_180)
r270 = cv2.rotate(img, cv2.ROTATE_90_COUNTERCLOCKWISE)
cv2.imshow("90 Degrees", r90)
cv2.imshow("180 Degrees", r180)
cv2.imshow("270 Degrees", r270)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 4. Image Brightness

```
import cv2
img = cv2.imread("image.jpg")
bright = cv2.convertScaleAbs(img, alpha=1, beta=50)
cv2.imshow("Original", img)
cv2.imshow("Bright", bright)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 5. Image Contrast

```
import cv2
img = cv2.imread("image.jpg")
contrast = cv2.convertScaleAbs(img, alpha=2, beta=0)
cv2.imshow("Original", img)
cv2.imshow("Contrast", contrast)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


## 6. Gaussian Blur

```
import cv2
img = cv2.imread("image.jpg")
blur = cv2.GaussianBlur(img, (15, 15), 0)
cv2.imshow("Blur", blur)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 7. Canny Edge Detection

```
import cv2
img = cv2.imread("image.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray, 100, 200)
cv2.imshow("Edges", edges)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 8. Image Thresholding

```
import cv2
img = cv2.imread("image.jpg", 0)
_, binary = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)
cv2.imshow("Binary Image", binary)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 9. Image Cropping

```
import cv2
img = cv2.imread("image.jpg")
crop = img[50:250, 50:250]
cv2.imshow("Cropped Image", crop)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 10. Red Color Detection

```
import cv2
img = cv2.imread("image.jpg")
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
mask1 = cv2.inRange(hsv, (0, 100, 100), (10, 255, 255))
mask2 = cv2.inRange(hsv, (170, 100, 100), (180, 255, 255))
mask = cv2.bitwise_or(mask1, mask2)
result = cv2.bitwise_and(img, img, mask=mask)
cv2.imshow("Red Detection", result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 11. Histogram Analysis

```
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("image.jpg", 0)
plt.hist(img.ravel(), 256, [0, 256])
plt.show()
```


## 12. Histogram Equalization

```
import cv2
img = cv2.imread("image.jpg", 0)
equalized = cv2.equalizeHist(img)
cv2.imshow("Original", img)
cv2.imshow("Equalized", equalized)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 13. Salt-and-Pepper Noise Removal

```
import cv2
import numpy as np
img = cv2.imread("image.jpg")
noise = img.copy()
noise[np.random.random(img.shape[:2]) < 0.02] = 0
noise[np.random.random(img.shape[:2]) > 0.98] = 255
filtered = cv2.medianBlur(noise, 3)
cv2.imshow("Filtered", filtered)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 14. Image Sharpening

```
import cv2
import numpy as np
img = cv2.imread("image.jpg")
kernel = np.array([[0, -1, 0], [-1, 5, -1], [0, -1, 0]])
sharp = cv2.filter2D(img, -1, kernel)
cv2.imshow("Sharpened", sharp)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 15. Contour Detection

```
import cv2
img = cv2.imread("image.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
_, binary = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)
contours, _ = cv2.findContours(binary, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
cv2.drawContours(img, contours, -1, (0, 255, 0), 2)
cv2.imshow("Contours", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 16. Erosion and Dilation

```
import cv2
img = cv2.imread("image.jpg", 0)
_, binary = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)
kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (3, 3))
erosion = cv2.erode(binary, kernel)
dilation = cv2.dilate(binary, kernel)
cv2.imshow("Erosion", erosion)
cv2.imshow("Dilation", dilation)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


## 17. Document Image Processing

```
import cv2
img = cv2.imread("image.jpg", 0)
blur = cv2.GaussianBlur(img, (5, 5), 0)
binary = cv2.adaptiveThreshold(
blur, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
cv2.THRESH_BINARY, 11, 2
)
cv2.imshow("Document", binary)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 18. Face Detection

```
import cv2
img = cv2.imread("image.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
face = cv2.CascadeClassifier(
cv2.data.haarcascades + "haarcascade_frontalface_default.xml"
)
faces = face.detectMultiScale(gray, 1.1, 5)
for x, y, w, h in faces:
cv2.rectangle(img, (x, y), (x+w, y+h), (0, 255, 0), 2)
cv2.imshow("Faces", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 19. Image Difference

```
import cv2
img1 = cv2.imread("image.jpg")
img2 = cv2.imread("image2.jpg")
img2 = cv2.resize(img2, (img1.shape[1], img1.shape[0]))
diff = cv2.absdiff(img1, img2)
gray = cv2.cvtColor(diff, cv2.COLOR_BGR2GRAY)
_, result = cv2.threshold(gray, 30, 255, cv2.THRESH_BINARY)
cv2.imshow("Difference", result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## 20. Green Color Segmentation

```
import cv2
img = cv2.imread("image.jpg")
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
mask = cv2.inRange(hsv, (25, 40, 40), (90, 255, 255))
result = cv2.bitwise_and(img, img, mask=mask)
cv2.imshow("Green Region", result)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
