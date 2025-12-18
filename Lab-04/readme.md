# Title: **Fundamentals of digital images and Basic image operation using Python**

##  **Objectives**

1. **Load and display** digital image
2. **Understand** the digital image representation
3. **Color** to Grayscale and binary image conversion
4. **Image Transformation** (Resize, Rotate, Flip)
5. **Crop** the ROI (Region of Interest) in an image 


---

#  **Background Theory**

## 1. Digital Image (Pixels & Resolution)

A **digital image** is a discrete representation of a visual scene stored as a 2D array (matrix) of picture elements called **pixels**. Each pixel represents the smallest unit of an image and contains intensity/color information.

### Key Concepts:

- **Pixel (Picture Element)**: The fundamental unit of a digital image. Each pixel stores a numerical value (0-255 for 8-bit images) representing intensity or color.

- **Image Dimensions**: Represented as Height × Width, measured in pixels
  - Example: A 1920×1080 image has 1920 pixels wide and 1080 pixels tall
  
- **Resolution**: The total number of pixels in an image
  - Formula: Resolution = Height × Width × Number of Channels
  - Higher resolution means more detail but larger file size

- **Color Depth/Bit Depth**: Number of bits used to represent each pixel
  - 8-bit: 256 possible values (0-255) per channel
  - 24-bit: 8 bits per channel for RGB (256³ = 16.7 million colors)
  
- **Pixel Coordinates**: Typically (x, y) or (row, column) notation
  - In OpenCV: Image[row, column] or Image[y, x] format
  - Origin (0,0) is at top-left corner

---

## 2. Color Models (RGB, Grayscale & Binary)

### RGB (Red, Green, Blue) Color Model

- **Definition**: Additive color model using three channels: Red, Green, and Blue
- **Representation**: Each pixel is represented by 3 values (R, G, B), each ranging 0-255
- **Total Colors**: 256³ = 16,777,216 possible colors (True Color)
- **Use Cases**: Display monitors, digital cameras, natural images
- **Advantages**: Human eye perceives red, green, blue light; most intuitive color representation
- **In OpenCV**: Stored as BGR (Blue, Green, Red) due to historical reasons

### Grayscale (Achromatic) Color Model

- **Definition**: Single-channel representation of image intensity/luminosity
- **Representation**: Each pixel has one value (0-255), where 0=black and 255=white
- **Conversion Formula**: Gray = 0.299×R + 0.587×G + 0.114×B (weighted average)
  - Weights account for human eye sensitivity to different colors
- **Total Colors**: 256 shades of gray
- **Use Cases**: Medical imaging, document scanning, image processing preprocessing
- **Advantages**: Reduced computational complexity, faster processing, smaller file size

### Binary (Black & White) Color Model

- **Definition**: Two-level (1-bit) image representation
- **Representation**: Each pixel is either 0 (black) or 255 (white)
- **Creation Method**: Thresholding operation on grayscale image
  - Pixels with intensity < threshold → 0 (black)
  - Pixels with intensity ≥ threshold → 255 (white)
- **Common Threshold Values**: 127 for mid-range, varies by application
- **Use Cases**: Document binarization, object detection, OCR (Optical Character Recognition)
- **Advantages**: Minimal storage, extreme contrast, suitable for specific applications

---

## 3. Image File Format

Digital images can be stored in various file formats, each with different characteristics:

### Common Image Formats:

| Format | Full Name | Compression | Use Cases |
|--------|-----------|-------------|-----------|
| **JPG/JPEG** | Joint Photographic Experts Group | Lossy | Photographs, natural images, web distribution |
| **PNG** | Portable Network Graphics | Lossless | Graphics, web images, transparency needed |
| **BMP** | Bitmap | Uncompressed | Simple images, Windows compatibility |
| **TIFF** | Tagged Image File Format | Lossless | Medical imaging, archival, publishing |
| **GIF** | Graphics Interchange Format | Lossless | Animations, simple graphics |

### Key Differences:

- **Lossy Compression** (JPG): Discards some data; smaller file size; quality loss
- **Lossless Compression** (PNG, BMP, TIFF): No data loss; preserves quality; larger file size
- **Uncompressed** (BMP): Raw pixel data; largest file size; fastest access

### File Structure:
- **Header**: Contains image metadata (dimensions, color depth, format info)
- **Color Table** (if applicable): Palette for indexed color images
- **Image Data**: Actual pixel values

---

## 4. Basic Image Transformation

Image transformation refers to operations that modify the spatial or intensity properties of an image.

### Spatial Transformations:

#### Resizing (Scaling)
- **Definition**: Change image dimensions to new height and width
- **Methods**:
  - **Nearest Neighbor**: Fast, pixelated appearance
  - **Bilinear Interpolation**: Smooth results, moderate computation
  - **Bicubic Interpolation**: Highest quality, slower
- **Formula**: New_pixel_position = scaling_factor × old_pixel_position
- **Application**: Normalize image sizes for processing, thumbnail generation

#### Rotation
- **Definition**: Rotate image by specified angle around a center point
- **Rotation Matrix**: 
  ```
  [cos(θ)  -sin(θ)]
  [sin(θ)   cos(θ)]
  ```
- **Parameters**: Center point, angle (degrees), scaling factor
- **Application**: Image alignment, perspective correction, data augmentation

#### Flipping
- **Horizontal Flip**: Mirror image along vertical axis (left↔right)
- **Vertical Flip**: Mirror image along horizontal axis (top↔bottom)
- **Application**: Data augmentation, image preprocessing, symmetry operations

### Cropping (ROI Extraction)
- **Definition**: Extract rectangular region of interest from image
- **Method**: Array slicing using coordinates [y1:y2, x1:x2]
- **Advantage**: Reduces image size, focuses on region of interest
- **Application**: Face detection, object localization, region analysis

---

## 5. Introduction to OpenCV

### What is OpenCV?

**OpenCV** (Open Source Computer Vision Library) is a free, open-source computer vision library written in C++ with Python bindings. It provides tools for image processing, video analysis, feature detection, and machine learning.

### Key Features:

- **Image I/O**: Read/write images in multiple formats
- **Image Processing**: Filtering, transformations, color space conversion
- **Video Processing**: Capture, process, and save video streams
- **Feature Detection**: Edge detection, corner detection, blob detection
- **Machine Learning**: Built-in ML algorithms for computer vision tasks
- **GPU Support**: CUDA acceleration for faster processing

### Core Functions Used in This Lab:

| Function | Purpose | Syntax |
|----------|---------|--------|
| `cv2.imread()` | Read image from file | `cv2.imread(filename)` |
| `cv2.imwrite()` | Save image to file | `cv2.imwrite(filename, image)` |
| `cv2.cvtColor()` | Convert color space | `cv2.cvtColor(img, code)` |
| `cv2.resize()` | Resize image | `cv2.resize(img, (width, height))` |
| `cv2.getRotationMatrix2D()` | Get rotation matrix | `cv2.getRotationMatrix2D(center, angle, scale)` |
| `cv2.warpAffine()` | Apply affine transformation | `cv2.warpAffine(img, matrix, (width, height))` |
| `cv2.flip()` | Flip image | `cv2.flip(img, flipCode)` |
| `cv2.threshold()` | Create binary image | `cv2.threshold(img, thresh, maxval, type)` |

### Image Representation in OpenCV:

- **Data Type**: Images are stored as NumPy arrays
- **Shape**: (Height, Width, Channels) for color images
- **Color Order**: BGR instead of RGB (important for conversion)
- **Pixel Values**: uint8 (0-255) for standard images

### Advantages of OpenCV:

1. **Cross-platform**: Works on Windows, Linux, macOS
2. **Multiple Language Support**: C++, Python, Java
3. **Comprehensive**: Covers most computer vision needs
4. **Efficient**: Optimized C++ backend
5. **Active Community**: Large user base and extensive documentation
6. **Integration**: Works well with NumPy, Matplotlib, SciPy
---
# **Procedure**

## 1: Reading and Displaying Images
- Used OpenCV (`cv2.imread()`) to load digital images in JPG format
- Converted color space from BGR (OpenCV default) to RGB for proper display
- Used Matplotlib to visualize the loaded image
- **Code Files**: `1.Read_n_display_img.ipynb`

## 2: Exploring Image Properties
- Analyzed image dimensions (height, width, channels)
- Examined image data types (uint8)
- Retrieved individual pixel values at specific locations
- Extracted and printed image metadata
- **Code Files**: `2.Explore_image.ipynb`

## 3: Color Space Conversion
- **Grayscale Conversion**: Used `cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)` to convert RGB to grayscale (single channel)
- **Binary Image Conversion**: Applied threshold operation `cv2.threshold()` with threshold value 127 to create binary images (black and white only)
- Saved converted images in both JPG and BMP formats
- **Code Files**: `3.Image_Conversion.ipynb`

## 4: Image Transformation Operations
- **Resize**: Reshaped images to 300x300 pixels using `cv2.resize()`
- **Rotate**: Rotated original image by 10 degrees around the center using `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`
- **Flip**: Applied horizontal flip operation using `cv2.flip(image, 1)`
- Verified dimensions and properties after each transformation
- **Code Files**: `4.Image_Transformation.ipynb`

## 5: Region of Interest (ROI) Extraction
- Cropped a rectangular region from the original image using array slicing: `image[50:200, 50:200]`
- Extracted 150x150 pixel ROI from specified coordinates
- Displayed cropped region separately using Matplotlib
- **Code Files**: `5.ROI_in_an_Image.ipynb`

---

#  **Output**

### Key Findings:

1. **Image Properties**:
   - Original Image: JPG format with 3 channels (RGB/BGR)
   - Dimensions: Height × Width × Channels format in OpenCV
   - Data type: uint8 (8-bit unsigned integers, values 0-255)
   - Pixel values range from 0-255 per channel

2. **Color Space Conversions**:
   - **Grayscale Images**: Successfully reduced 3-channel color images to 1-channel grayscale using weighted average of RGB components
   - **Binary Images**: Applied threshold operation converted all pixels to either 0 (black) or 255 (white) based on threshold value of 127

3. **Image Transformations**:
   - **Resizing**: Reduced image dimensions while maintaining aspect ratio or scaling to exact target size
   - **Rotation**: Successfully rotated image by specified angle (10°) around center point
   - **Flipping**: Horizontal flip operation mirrored the image along vertical axis

4. **ROI Extraction**:
   - Successfully cropped rectangular regions from images using coordinate-based slicing
   - ROI extraction preserves all channels and data types of original image

5. **File Format Compatibility**:
   - Images successfully saved in multiple formats (JPG, BMP)
   - OpenCV handles format conversion automatically during write operations
   - Different formats may have different compression characteristics

---

#  **Conclusion**

This laboratory successfully demonstrated the fundamental operations for digital image processing using Python and OpenCV:

1. **Digital Image Understanding**: 
   - Verified that digital images are represented as 3D arrays (height × width × channels)
   - Confirmed pixel values are stored as 8-bit unsigned integers (0-255 range)
   - Demonstrated understanding of color models (RGB/BGR, Grayscale, Binary)

2. **Image Processing Capabilities**:
   - Successfully loaded, displayed, and saved images in various formats
   - Implemented color space conversions (RGB↔BGR, Color↔Grayscale, Color↔Binary)
   - Applied geometric transformations (resize, rotate, flip)
   - Extracted regions of interest using array slicing techniques

3. **OpenCV Library Proficiency**:
   - Utilized core OpenCV functions (`imread`, `cvtColor`, `resize`, `rotate`, `flip`, `threshold`)
   - Integrated OpenCV with Matplotlib for visualization
   - Applied proper coordinate systems and transformation matrices

4. **Practical Applications**:
   - Image preprocessing for machine learning pipelines
   - Format conversion for compatibility across platforms
   - Feature extraction through ROI identification
   - Image enhancement through transformations

The laboratory objectives were successfully achieved. Students demonstrated competency in loading, analyzing, converting, transforming, and extracting regions from digital images using Python and OpenCV libraries.

---
