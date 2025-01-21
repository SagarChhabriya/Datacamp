# Image Processing in Python

## Image Processing
It is a subset of computer vision. Image processing are operations on image and videos to:

- Enhance an image
- Extract useful information
- Analyze it and make decision

## Purpose
1. Visualization
    - Objects that aren't visible.
2. Image Sharpening and Restoration
    - A better image
3. Image retrieval
    - Seek for image of interest
4. Measurements of Pattern
    - Measures various objects
5. Image Recognition
    - Distinguish objects in an image 


## What is an image?
A 2-dimensional array of pixels.

![image](https://github.com/user-attachments/assets/cfa34ad1-8133-4595-96a8-33e772c95011)

```python
# pip install scikit-image
from skimage import data, color
import matplotlib.pyplot as plt

def show_image(image, title='Image', cmap_type='gray'):
    plt.imshow(image, cmap=camp_type)
    plt.title(title)
    plt.axis('off')
    plt.show()

# Load Rocket image
rocket = data.rocket() 

# Show image
show_image(rocket, 'original rgb image')

# Convert & Show gray scale image
gray_scaled = color.rgb2gray(rocket)

show_image(gray_scaled,'Gray_img')
```

![image](https://github.com/user-attachments/assets/fef6e2b3-8886-4205-9dae-f32f46af2c29)


### Example 2: RGB vs GrayScale

```python
from skimage import color
grayscale = color.rgb2gray(original)
rgb = color.gray2rgb(grayscale)
```

![image](https://github.com/user-attachments/assets/9543ccdc-c5d0-4c1f-95ad-b36d77e69a21)


## Numpy for Images

Fundamentals of image processing techniques.
- Flipping
- Extract & analyze features

![image](https://github.com/user-attachments/assets/599aeff9-88bb-402c-bf99-5176fdf66caa)

### Images as ndarrays

```python
# Load image using matplotlib
madrid_image = plt.imread('/madrid.jpeg')
type(madrid_image)
```


### Colors with numpy

```python
# Accessing image shape
madrid_image.shape
(426,640, 3) # (Rows, cols, color: 3-RGB)

# Pixels of image
madrid_image.size
817920

# Obtaining red values of image
red = image[:, :, 0]

# green values
green = image[:, : , 1]

# blue values
blue = image[:, :, 2]

```

### Flipping Image

```python
# Flip image vertically
vertical = np.flipud(image)
show_image(vertical)

# Flip horizontally
horizontal = np.fliplr(image)
show_image(horizontal)

```


## What is histogram?
A graph that shows distributions of pixels in an aimage based on their intensity.

- Applications of histogram
    - Analysis
    - Thresholding
    - Brightness & Contrast
    - Equalize an image

## Histogram in Matplotlib

```python
# Red color of the image
red = image[:, :, 0]

# Obtain red histogram
plt.hist(red.ravel(), bins=256)
plt.show()
```


## Thresholding 
Thresholding is an image processing technique that separates an image into two regions: a foreground and a background. It works by converting grayscale or color images into binary images, where each pixel is either black or white. We do so by setting each pixel to:

- 255(white) if pixel > threshValue
- 0(black) if pixel < threshValue

### Thresholding is a simplest method of image segmentation
- Isolate objects
    - Object detection
    - Face detection, etc 

![image](https://github.com/user-attachments/assets/726df51b-f19c-4010-b6a5-c59cbc176786)

![image](https://github.com/user-attachments/assets/fb2ef3f1-738f-4019-91c6-b6b603103f63)

## Types of Thresholding
1. Global or histogram based
  - Good for uniform backgrounds
2. Local or adaptive 
  - For uneven background illumination

![image](https://github.com/user-attachments/assets/f084150f-bded-4aef-8a16-8ff3a27a7be7)

![image](https://github.com/user-attachments/assets/54d360e9-d7a0-4eed-b3b4-ba66166fb4ea)

## Global Thresholding

![image](https://github.com/user-attachments/assets/bb32dbd6-95ca-412f-acec-ef0dba283b08)

![image](https://github.com/user-attachments/assets/8a3ff214-9343-4e68-9afe-4177e442d99d)

## Local Thresholding 

![image](https://github.com/user-attachments/assets/0fbb8146-de5f-4880-9577-bfbee81e3754)

![image](https://github.com/user-attachments/assets/c5724785-aebf-4842-b3d4-4fc5d9ccc54b)

