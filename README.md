# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

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

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.png` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt


gray = cv2.imread("parrot.png", cv2.IMREAD_GRAYSCALE)

if gray is None:
    print("Error: parrot.png not found.")
    exit()

gray_eq = cv2.equalizeHist(gray)

plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(gray, cmap='gray')
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(gray.ravel(), 256, [0, 256], color='black')
plt.title("Original Histogram")

plt.subplot(2, 2, 3)
plt.imshow(gray_eq, cmap='gray')
plt.title("Equalized Grayscale Image")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.hist(gray_eq.ravel(), 256, [0, 256], color='black')
plt.title("Equalized Histogram")

plt.tight_layout()
plt.show()

img = cv2.imread("parrot.png")

if img is None:
    print("Error: parrot.png not found.")
    exit()

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(img_rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(2, 2, 2)

colors = ('b', 'g', 'r')
for i, col in enumerate(colors):
    hist = cv2.calcHist([img], [i], None, [256], [0, 256])
    plt.plot(hist, color=col)

plt.title("Original RGB Histogram")
plt.xlim([0, 256])

hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

h, s, v = cv2.split(hsv)
v_eq = cv2.equalizeHist(v)

hsv_eq = cv2.merge((h, s, v_eq))

result = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)

result_rgb = cv2.cvtColor(result, cv2.COLOR_BGR2RGB)

plt.subplot(2, 2, 3)
plt.imshow(result_rgb)
plt.title("Equalized Color Image")
plt.axis("off")

plt.subplot(2, 2, 4)

for i, col in enumerate(colors):
    hist = cv2.calcHist([result], [i], None, [256], [0, 256])
    plt.plot(hist, color=col)

plt.title("Equalized RGB Histogram")
plt.xlim([0, 256])

plt.tight_layout()
plt.show()
```

### Developed By:
### **Name: MOHIT N** 

### **Register No: 212225040255**

---

##  Output

<img width="1352" height="548" alt="image" src="https://github.com/user-attachments/assets/2cc80c6c-243a-484b-9581-c1dbf8b7d21b" />

<img width="1342" height="558" alt="image" src="https://github.com/user-attachments/assets/8d84ec47-f96a-4e31-bc73-2b60db4f6f54" />

<img width="1340" height="550" alt="image" src="https://github.com/user-attachments/assets/4af17690-7768-4136-9b94-4f5ddad59417" />

<img width="1318" height="542" alt="image" src="https://github.com/user-attachments/assets/681cfb19-6d44-495b-acd8-d44a28026147" />






### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
