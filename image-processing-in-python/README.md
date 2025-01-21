![image](https://github.com/user-attachments/assets/fb81442e-f1f3-4031-a04e-364682e27510)# Image Processing in Python

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


---

## Chapter 2: Filtering, Contrast, Transformations, and Morphology


- Filtering: Image filtering is a technique that `changes the appearance of an image by adjusting the colors of its pixels`. The goal is to enhance certain features, remove others, or reduce noise.
- Contrast in image processing is `the difference in color or grayscale between different parts of an image`. It's a key factor in image quality, as it helps make images easier to see and understand.
- Image transformations in image processing `change the shape or pixel values of an image.`
- Morphology in image processing is a `set of techniques that analyze and modify images based on their shape and structure.`

---
# Image Transformations in Image Processing

Image transformations in image processing change the shape or pixel values of an image. Some common types of image transformations include:

## Affine Transformation
An **affine transformation** is a geometric transformation that combines translation, rotation, scaling, and shearing. It preserves the ratio between points and the perpendicularity of line pairs.

## Perspective Transformation
A **perspective transformation** is a geometric transformation that changes the pixel coordinates of an image, often used to simulate the view from different angles or depths.

## Piece-wise Linear Transformation
A **piece-wise linear transformation** is a spatial domain method that manipulates an image to make it more suitable for specific applications by adjusting pixel values within specified regions.

## Log Transformation
A **log transformation** is an image enhancement technique that replaces each pixel value with its logarithmic value. This transformation is useful for expanding dark pixels in the image, making details more visible in low-intensity areas.

## Fourier Transform
A **Fourier transform** is a technique that transforms an image's intensity into frequency variation. It's commonly used for analyzing images with low varying intensities or in frequency domain filtering.

## Image Rotation
**Image rotation** is a transformation that changes the shape of an image by rotating it by a specified angle. It is widely used in geometric transformations to reorient an image.

## Reflection
**Reflection** is a geometric operation that flips an image across a specific axis, resulting in a mirrored version of the original image.

## Matrix Transformation
A **matrix transformation** is a linear algebra operation that combines multiple linear transformations (like translation, scaling, rotation) into a single transformation matrix. This is commonly used in more advanced image manipulation techniques.

---
# Morphology in Image Processing

Morphology in image processing is a set of techniques that analyze and modify images based on their shape and structure. These techniques are based on mathematical morphology, which is the study of shapes and patterns.

## How It Works
1. A **structuring element**, which is a small matrix, is applied to an input image.
2. The value of each pixel in the output image is based on how the corresponding pixel in the input image compares to its neighbors.
3. The **shape and size** of the structuring element significantly impact the outcome of the operation.

## What It's Used For
- **Pattern Recognition**: Morphological image processing is used to recognize patterns in images.
- **Image Segmentation**: Morphological techniques are used to segment images into different parts.
- **Feature Extraction**: These techniques can be used to extract specific features from images.
- **Noise Removal**: Morphological image processing helps to remove noise from images.
- **Shape Separation**: It is used to separate different shapes or objects within an image.

## Some Examples of Morphological Operations
- **Erosion**
- **Dilation**
- **Opening**
- **Closing**
- **Geodesic Dilation**
- **Hysteresis Thresholding**


---

### 1. Filters

Filtering is a technique for modifying or enhancing an image. In essence, a filter is a mathematical function that is applied to images. It can be used to emphasize or remove certain features, like edges. Smoothing, sharpening, and edge detection. In this video we will cover smoothing and edge detection. Filtering is a neighborhood operation, let's see what that means.

---

### 2. Neighborhoods

Certain image processing operations involve processing an image in sections, called blocks or neighborhoods, rather than processing the entire image at once. This is the case for filtering, histogram equalization for contrast enhancement, and morphological functions, all three of which use this approach.

![image](https://github.com/user-attachments/assets/89007cde-98e6-4bee-8656-15f9c210168d)

---

### 3. Edge detection

So, with filtering we can detect edges. This technique can be used to find the boundaries of objects within images. As well as segment and extract information like how many coins are in an image. Most of the shape information of an image is enclosed in edges.

![image](https://github.com/user-attachments/assets/85ed7b44-7589-4c6a-a86e-e6e331765667)

Edge detection works by detecting discontinuities in brightness. Like in this image, where we spot the chocolate kisses shapes in the image.


![image](https://github.com/user-attachments/assets/57953308-391d-42f9-8255-120a1df24698)


A common edge detection algorithm is Sobel. This is a filter that we can find in scikit-image's module filters with the sobel function. The previously used coins image is preloaded as `image_coins`. We apply the filter by passing the image we want to detect the edges from as a parameter. This function requires a 2-dimensional grayscale image as input. So in the case of a colored image, we'll need to convert it to grayscale first. Then, we show the original and the resulting image with a function that uses Matplotlib subplots.


![image](https://github.com/user-attachments/assets/b6e0495b-4c4d-4d4a-b622-68af75d3411c)


So we see that the filter is detecting the edges in the original image and highlighting the boundaries as closed lines in the resulting image.

![image](https://github.com/user-attachments/assets/3b05fbb6-19ce-45f9-b238-05ca3e4f0570)

---

### 4. Comparing plots

This is the plot comparison function we just used. It plots the original image next to the resulting one. Using this function allows us to reuse this code and focus more on the image processing part of the code.



---

### 5. Gaussian smoothing

Let's look at another filtering technique, smoothing. We can achieve this with a Gaussian filter. This technique is typically used to blur an image or to reduce noise. Here we see the effect of applying a Gaussian filter, which can especially be seen in the edges of the dog's hair. The Gaussian filter will blur edges and reduce contrast. This is used in other techniques like anti-aliasing filtering.


---

### 6. Gaussian smoothing


Let's see how we can do this with Scikit-image using this picture of me in Amsterdam.



We import the Gaussian function from the filters module of scikit-image. To apply the filter, the original image is passed as the first parameter to the Gaussian function and the multichannel boolean parameter is set to `True` if the image is colored, otherwise it needs to be set to `False`. Finally, let's compare the original and the resulting image.

Sometimes when the image is too large, meaning it has a big resolution, we do not easily see the effect. Let's look more closely at the image.

Here, we can see more clearly how the Gaussian filter is blurring the image and removing the noise.


---

## 1. Contrast Enhancement
Now that we have seen what histograms are, we will look at one of its applications in image enhancement.

Image enhancement can be extremely useful in multiple areas. Often, medical images like this X-ray can have low contrast, making it hard to spot important details. When we improve the contrast, the details become more visible. It's definitely easier to spot things on this one!

The contrast of an image can be seen as the measure of its dynamic range, or the "spread" of its histogram. Consider this image. The contrast is the difference between the maximum and minimum pixel intensity in the image. The histogram of this image is shown on the right. The maximum value of pixel intensity is 255 while the minimum is 0. 255 - 0 = 255.

An image of low contrast has a small difference between its dark and light pixel values. It is usually skewed either to the right (mostly light), to the left (mostly dark), or located around the middle (mostly gray).

![image](https://github.com/user-attachments/assets/e1eac8f3-ddbb-4d67-9618-d513f1253638)

![image](https://github.com/user-attachments/assets/86a3559b-016f-44b4-afb6-e1e57d2994ba)

![image](https://github.com/user-attachments/assets/81c91203-0c31-4f94-93e4-3fa7fb9362cb)

## 2. Enhance Contrast
We can enhance contrast through `contrast stretching`, which is used to stretch the histogram so the full range of intensity values of the image is filled. And `histogram equalization`, which spreads out the most frequent histogram intensity values using probability distribution. We'll cover histogram equalization in this video.

## 3. Types
In general, there are three types of histogram equalization: the standard, the adaptive, and the limited adaptive. In scikit-image, we can apply standard histogram equalization, contrast stretching, and contrast-limited adaptive as we can see in these images.

![image](https://github.com/user-attachments/assets/b4274cf6-a5b0-467b-bd47-7bc2e74d910f)


## 4. Histogram Equalization
As we have seen, histogram equalization spreads out the most frequent intensity values. Let's start by taking this image as a simple image.
![image](https://github.com/user-attachments/assets/7289740c-a541-4737-9cd2-714d3e521804)

## 9. Histogram Equalization
To apply this type of histogram equalization, import the exposure module from scikit-image. We then have access to all equalization methods. In this case, the `equalize_hist` function applies normal histogram equalization to the original image. Then, we show both images, the original and equalized one, to see the difference.

![image](https://github.com/user-attachments/assets/1b239d8e-29d0-404f-92e8-6cf1e76739a7)

![Uploading image.png…]()

## 10. Histogram Equalization
We get a result that, despite the increased contrast, doesn't look natural. In fact, it doesn't even look like the image has been enhanced at all.

## 11. Adaptive Equalization
Another type of histogram equalization is the adaptive one. This method computes several histograms, each corresponding to a distinct part of the image, and uses them to redistribute the lightness values of the image histogram. A type of this method is the Contrastive Limited Adaptive Histogram Equalization (CLAHE), which was developed to prevent over-amplification of noise that adaptive histogram equalization can give rise to. In this image, we see the result of the CLAHE method, and it may seem very similar to the standard method.

## 12. Contrastive Limited Adaptive Equalization
But if you look closer and compare the results, you will see that the adaptive method is not as intense, so it looks more natural. This is because it is not taking the global histogram of the entire image, but operates on small regions called tiles or neighborhoods.

## 13. CLAHE in scikit-image
To apply this kind of adaptive equalization, we can use the `equalize_adapthist` function provided by scikit-image. It calculates the contrast transform function for each tile individually. We pass the original image as the first parameter and a `clip_limit`. This clipping limit is normalized between 0 and 1 (higher values give more contrast). Then, show the original and resulting images.

## 14. CLAHE in scikit-image
Comparing them, the resulting image is enhanced, and we can better detail small objects and figures, like the footprints on the ground.
