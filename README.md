# Exp-6--Record-EDGE-DETECTION


## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---
# Program

## Developed By

###  **Name:** DIVYA PRIYA S  
### **Register No:** 212225240037
---
### Original Image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"C:\Users\acer\OneDrive\Pictures\Screenshots\FLOWER.png") 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
### Sobel Edge Detector
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  # Sobel in x direction
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  # Sobel in y direction
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  # Combine both directions
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')

```
### Laplacian Edge Detector 
```
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
```
### Canny Edge Detector
```
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')  
```
### Roberts Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
image = cv2.imread(r"C:\Users\acer\OneDrive\Pictures\Screenshots\FLOWER.png", 0)

# Check image
if image is None:
    print("Image not found. Check the file path.")
else:
    # Roberts kernels
    roberts_x = np.array([[1, 0],
                          [0, -1]])

    roberts_y = np.array([[0, 1],
                          [-1, 0]])

    # Apply Roberts filters
    gx = cv2.filter2D(image, cv2.CV_64F, roberts_x)
    gy = cv2.filter2D(image, cv2.CV_64F, roberts_y)

    # Calculate edge magnitude
    roberts = cv2.magnitude(gx.astype(np.float32),
                            gy.astype(np.float32))

    # Display
    plt.imshow(roberts, cmap='gray')
    plt.title("Roberts Edge Detector")
    plt.axis("off")
    plt.show()
 ```
### Prewitt Edge Detector
 ```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
image = cv2.imread(r"C:\Users\acer\OneDrive\Pictures\Screenshots\FLOWER.png", 0)

# Check image
if image is None:
    print("Image not found. Check the file path.")
else:
    # Prewitt kernels
    prewitt_x = np.array([[-1, 0, 1],
                          [-1, 0, 1],
                          [-1, 0, 1]])

    prewitt_y = np.array([[-1, -1, -1],
                          [ 0,  0,  0],
                          [ 1,  1,  1]])

    # Apply Prewitt filters
    gx = cv2.filter2D(image, cv2.CV_64F, prewitt_x)
    gy = cv2.filter2D(image, cv2.CV_64F, prewitt_y)

    # Calculate edge magnitude
    prewitt = cv2.magnitude(gx.astype(np.float32),
                            gy.astype(np.float32))

    # Display result
    plt.imshow(prewitt, cmap='gray')
    plt.title("Prewitt Edge Detector")
    plt.axis("off")
    plt.show()
```
    
# Output

### Original Image

<img width="611" height="480" alt="Screenshot 2026-11-01 004045" src="https://github.com/user-attachments/assets/1ccfcffb-5d9c-400c-ae9d-682801e5ed3b" />


###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map
<img width="590" height="34" alt="Screenshot 2026-11-01 004526" src="https://github.com/user-attachments/assets/7b8e8e33-d650-471a-86a2-f2204359f8ca" />
<img width="433" height="669" alt="Screenshot 2026-11-01 003906" src="https://github.com/user-attachments/assets/e478a03f-ab7b-42c3-8024-1adb16e84449" />

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  
<img width="421" height="658" alt="Screenshot 2026-11-01 004018" src="https://github.com/user-attachments/assets/00b0f94d-c87c-44ce-b681-730c74f1aa83" />

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  
<img width="410" height="660" alt="Screenshot 2026-11-01 004008" src="https://github.com/user-attachments/assets/b1e966aa-9c9a-487e-9db1-b315a7d06ebc" />

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes
<img width="669" height="32" alt="image" src="https://github.com/user-attachments/assets/df47466a-eaa4-4081-b496-44d9783f50ea" />

<img width="393" height="664" alt="Screenshot 2026-11-01 003930" src="https://github.com/user-attachments/assets/f7ef704a-6313-49ea-8614-0b2b7e74bf78" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges
<img width="823" height="46" alt="Screenshot 2026-11-01 004726" src="https://github.com/user-attachments/assets/8c5442bc-2f9c-4fd4-8929-a8b4dcf7469e" />
<img width="417" height="666" alt="Screenshot 2026-11-01 003946" src="https://github.com/user-attachments/assets/4455b0c1-f5a7-4b86-a539-cf1ce1f2379f" />

---

# Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
