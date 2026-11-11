
# Exp-6 Edge Detection Using OpenCV

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

---

## Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply the **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply the **Prewitt operator** using custom kernels.

### Step 6:
Apply the **Roberts operator** using custom kernels.

### Step 7:
Apply the **Laplacian operator** using OpenCV.

### Step 8:
Apply the **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Output

### 1. Sobel Edge Detector

- Detects edges in horizontal and vertical directions.
- Produces a gradient-based edge map.

```.py
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread("C:\\Users\\admin\\Downloads\\plane.jpg") 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```

<img width="535" height="420" alt="image" src="https://github.com/user-attachments/assets/864626a2-2b52-4a8f-87af-64977b8a00a5" />


### 2. Prewitt Edge Detector

- Similar to Sobel but uses simpler kernels.
- Detects directional edges.

```.py
image = cv2.imread(r"C:\Users\admin\Downloads\plane.jpg")

if image is None:
    print("Error: Image not found")
else:
    # Convert to grayscale
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # Prewitt X and Y kernels
    prewitt_x = np.array([[-1, 0, 1],
                          [-1, 0, 1],
                          [-1, 0, 1]])

    prewitt_y = np.array([[-1, -1, -1],
                          [ 0,  0,  0],
                          [ 1,  1,  1]])

    # Apply Prewitt filters
    prewitt_x_edge = cv2.filter2D(gray, cv2.CV_32F, prewitt_x)
    prewitt_y_edge = cv2.filter2D(gray, cv2.CV_32F, prewitt_y)

    # Calculate edge magnitude
    prewitt = cv2.magnitude(prewitt_x_edge, prewitt_y_edge)

    # Display result
    plt.imshow(prewitt, cmap='gray')
    plt.title('Prewitt Edge Detection')
    plt.axis('off')
    plt.show()

```

<img width="592" height="430" alt="image" src="https://github.com/user-attachments/assets/f3eda8af-3319-47ba-859a-6bb8192a0295" />


### 3. Roberts Edge Detector

- Detects edges using diagonal gradients.
- Sensitive to noise.
```.py
image = cv2.imread(r"C:\Users\admin\Downloads\plane.jpg")

if image is not None:
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    rx = np.array([[1, 0], [0, -1]], dtype=np.float32)
    ry = np.array([[0, 1], [-1, 0]], dtype=np.float32)

    x = cv2.filter2D(gray, cv2.CV_32F, rx)
    y = cv2.filter2D(gray, cv2.CV_32F, ry)

    result = cv2.convertScaleAbs(cv2.magnitude(x, y))

    plt.imshow(result, cmap='gray')
    plt.title("Roberts Edge Detection")
    plt.axis('off')
    plt.show()
else:
    print("Image not found")

```

<img width="558" height="425" alt="image" src="https://github.com/user-attachments/assets/5091acb1-30ab-4fb9-a149-b8179e6a47b3" />





### 4. Laplacian Edge Detector

- Detects edges using second-order derivatives.
- Highlights rapid intensity changes.

```.py
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_8bit = cv2.convertScaleAbs(laplacian)
plt.imshow(laplacian_8bit, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```

<img width="550" height="420" alt="image" src="https://github.com/user-attachments/assets/0e819ab8-5b5d-4e2f-b60e-f026963c94d1" />


### 5. Canny Edge Detector

- Uses a multi-stage edge detection process.
- Produces clean and thin edges.
```.py
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```

<img width="542" height="420" alt="image" src="https://github.com/user-attachments/assets/f3a46431-72d2-4503-9beb-9c3d73ca6999" />


---

## Developed By:

#### Name: Jeyaarikaran.P
#### Register No.: 212224240064




---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and image analysis.
