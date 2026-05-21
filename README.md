# Record-Histogram-processing
## Name: HARINI S
## Register No:212224240049

## Aim
To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image
- Plot histogram of the grayscale image
- Apply histogram equalization on grayscale image
- Read and display a color image
- Plot histogram of B, G, R channels
- Convert image to HSV color space
- Apply histogram equalization on the Value (V) channel
- Convert the enhanced image back to BGR format
- Display original and enhanced images with histograms

## Software Used
Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib
 
## Algorithm

Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:
Read the image parrot.jpg in grayscale format.

Step 3:
Display the grayscale image and plot its histogram.

Step 4:
Apply histogram equalization using cv2.equalizeHist() to enhance contrast.

Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

Step 6:
Read the same image in color format.

Step 7:
Split the image into B, G, R channels and plot their histograms.

Step 8:
Convert the image from BGR to HSV color space.

Step 9:
Apply histogram equalization on the V (Value) channel.

Step 10:
Merge the channels and convert the image back to BGR format.

Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

# Program

# Grayscale Histogram Equalization 

```
# Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image in grayscale format
img = cv2.imread('parrot.jpg', 0)

# Check if image is loaded
if img is None:
    print("Error: Image not found!")
    exit()

# Plot histogram of original image
plt.figure(figsize=(8,6))
plt.hist(img.ravel(), 256, [0,256])
plt.title("Histogram of Original Image")
plt.show()

# Perform histogram equalization
equalized_img = cv2.equalizeHist(img)

# Display using 2x2 layout
plt.figure(figsize=(10,8))

# Original Image
plt.subplot(2,2,1)
plt.imshow(img, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis('off')

# Histogram of Original Image
plt.subplot(2,2,2)
plt.hist(img.ravel(), 256, [0,256])
plt.title("Original Histogram")

# Equalized Image
plt.subplot(2,2,3)
plt.imshow(equalized_img, cmap='gray')
plt.title("Enhanced Image")
plt.axis('off')
```
# Histogram of Equalized Image
```
plt.subplot(2,2,4)
plt.hist(equalized_img.ravel(), 256, [0,256])
plt.title("Enhanced Histogram")

plt.tight_layout()
plt.show()

# Color Histogram Equalization (HSV Method)
# Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the color image
img = cv2.imread('parrot.jpg')

# Check if image is loaded
if img is None:
    print("Error: Image not found!")
    exit()

# Convert BGR to RGB for display
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Plot histogram for B, G, R channels
colors = ('b','g','r')
plt.figure(figsize=(8,6))
for i, col in enumerate(colors):
    hist = cv2.calcHist([img],[i],None,[256],[0,256])
    plt.plot(hist, color=col)
plt.title("Histogram of Original Color Image")
plt.show()

# Convert to HSV
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

# Split channels
h, s, v = cv2.split(hsv)

# Equalize only the V channel (brightness)
v_eq = cv2.equalizeHist(v)

# Merge channels
hsv_eq = cv2.merge([h, s, v_eq])

# Convert back to BGR
img_eq = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)

# Convert to RGB for display
img_eq_rgb = cv2.cvtColor(img_eq, cv2.COLOR_BGR2RGB)

# Display using 2x2 layout
plt.figure(figsize=(10,8))

# Original Image
plt.subplot(2,2,1)
plt.imshow(img_rgb)
plt.title("Original Color Image")
plt.axis('off')

# Original Histogram
plt.subplot(2,2,2)
for i, col in enumerate(colors):
    hist = cv2.calcHist([img],[i],None,[256],[0,256])
    plt.plot(hist, color=col)
plt.title("Original Histogram")

# Enhanced Image
plt.subplot(2,2,3)
plt.imshow(img_eq_rgb)
plt.title("Enhanced Color Image")
plt.axis('off')

# Enhanced Histogram
plt.subplot(2,2,4)
for i, col in enumerate(colors):
    hist = cv2.calcHist([img_eq],[i],None,[256],[0,256])
    plt.plot(hist, color=col)
plt.title("Enhanced Histogram")

plt.tight_layout()
plt.show()
```
## Output

## Grayscale Histogram Equalization

<img width="590" height="449" alt="image" src="https://github.com/user-attachments/assets/6646adc9-e9c5-440c-bb45-552ecf1e6447" /><BR>
<img width="290" height="221" alt="image" src="https://github.com/user-attachments/assets/6d0b49f4-4778-49b5-8909-f5ced7da6fed" /><BR>

<img width="268" height="225" alt="image" src="https://github.com/user-attachments/assets/433c268f-f473-4cd0-9103-75229cbcb1b2" /><BR>
<img width="326" height="258" alt="image" src="https://github.com/user-attachments/assets/406f80cd-bd64-4a84-9134-f8cc225af935" /><BR>
## Color Histogram Equalization (HSV Method)
<img width="609" height="445" alt="image" src="https://github.com/user-attachments/assets/202f58d1-71d0-47ac-9f77-b517c78b0d3c" /><BR>

<img width="284" height="201" alt="image" src="https://github.com/user-attachments/assets/a9fbcdf3-249d-4ff6-8a21-0d4e1bdd3eb3" /><BR>


<img width="247" height="188" alt="image" src="https://github.com/user-attachments/assets/94e0d195-befd-460c-9ab5-a131c719895f" /><BR>

<img width="342" height="266" alt="image" src="https://github.com/user-attachments/assets/fc8d5e62-c4e5-4910-80de-11e9253483aa" /><BR>

Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.

