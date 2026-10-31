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
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"C:\Users\acer\OneDrive\Pictures\Screenshots\FLOWER.png")  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"C:\Users\acer\OneDrive\Pictures\Screenshots\FLOWER.png")  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
```
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
```
```
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')  
```
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
    
## Output

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
