# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** [ THARUNISH VASAN T]  
- **Register Number:** [ 212224240174 ]

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
img = cv2.imread('Eagle_in_Flight.jpg', cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img, cmap='gray')  
plt.title("Original Image")
plt.axis('off') 
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
res = cv2.imwrite('Eagle_in_Flight.png', img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_clr = cv2.imread('Eagle_in_Flight.png', cv2.IMREAD_COLOR)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_clr, cmap='viridis') 
plt.title("Original Image")
plt.axis('on') 
plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python

y,x,h,w = 0, 200, 430, 370
crop_img = img_clr[y:y+h, x:x+w]
plt.imshow(crop_img, cmap='viridis')
plt.title("Cropped Image") 
plt.axis('on')
plt.show()

```

#### 8. Resize the image up by a factor of 2x.
```python
resize_img = cv2.resize(img_clr, None, fx=2, fy=2)
plt.imshow(resize_img, cmap='viridis')
plt.title("Resized Image")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip_img = cv2.flip(img_clr, 1)
plt.imshow(flip_img, cmap='viridis')
plt.title("Flipped Image")
plt.axis('on')
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img2 = cv2.imread('Apollo-11-launch.jpg', cv2.IMREAD_COLOR)
plt.imshow(img2, cmap='viridis')
plt.title("Second Image") 
plt.axis('on')
plt.show()
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = 'Apollo 11 Saturn V Launch, July 16, 1969 - Ashqar'
font_face = cv2.FONT_HERSHEY_PLAIN
img2 = cv2.putText(img2, text, (300, 690), font_face, 1.5, (255, 255, 255), 2)
plt.imshow(img2, cmap='viridis')
plt.title("Image with Text")
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
#rect_color = magenta
img_rect = cv2.rectangle(img2, (400, 70), (800, 700), (255, 0, 255), 2)

```

#### 13. Display the final annotated image.
```python
plt.imshow(img_rect, cmap='viridis')
plt.title("Image with Text and Rectangle")
```

#### 14. Read the image ('Boy.jpg').
```python
img3 = cv2.imread('boy.jpg', cv2.IMREAD_COLOR)
plt.imshow(img3, cmap='viridis')
plt.title("Original Image")
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
matrix_ones = np.ones(img3.shape, dtype=np.uint8)*50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)

```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10, 5))
plt.subplot(1, 3, 1)
plt.imshow(img3, cmap='viridis')
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(img_brighter, cmap='viridis')
plt.title("Brighter Image")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(img_darker, cmap='viridis')
plt.title("Darker Image")
plt.axis('off')
```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
con_1 = cv2.convertScaleAbs(img3, alpha=1.1, beta=0)
con_2 = cv2.convertScaleAbs(img3, alpha=1.2, beta=0)

# Lower contrast images:
con_3 = cv2.convertScaleAbs(img3, alpha=0.7, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(img3, cmap='viridis')
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(con_3, cmap='viridis')
plt.title("Higher Contrast Image (0.7)")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(con_2, cmap='viridis')
plt.title("Higher Contrast Image (1.2)")
plt.axis('off')
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
B,G,R = cv2.split(img3)

plt.figure(figsize=(15,5))
plt.subplot(1, 3, 1)
plt.imshow(B)
plt.title("Blue Channel")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(G)
plt.title("Green Channel")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(R)
plt.title("Red channel")
plt.axis('off')
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_img = cv2.merge((R, G, B))

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(img3, cmap='viridis')
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(merged_img, cmap='viridis')
plt.title("Merged Image")
plt.axis('off')
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img3, cv2.COLOR_BGR2HSV)

h,s,v = cv2.split(hsv_img)
plt.figure(figsize=(15, 5))
plt.subplot(1, 3, 1)
plt.imshow(h, cmap='viridis')
plt.title("Hue Channel")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(s, cmap='viridis')
plt.title("saturation channel")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(v, cmap='viridis')
plt.title("Value channel")
plt.axis('off')
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged2_img = cv2.merge((h, s, v))

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(img3, cmap='viridis')
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(merged2_img, cmap='viridis')
plt.title("Merged Image")
plt.axis('off')
```

## Output:
- **i)** Read and Display an Image.  
      <img width="768" height="600" alt="Eagle_in_Flight" src="https://github.com/user-attachments/assets/4c20187c-b80a-44a6-8935-715ac958cedc" />

- **ii)** Adjust Image Brightness.  
      <img width="1182" height="298" alt="WhatsApp Image 2026-05-11 at 2 05 38 PM" src="https://github.com/user-attachments/assets/0d12de15-71b7-4ee9-97dd-f8886eef3b52" />

- **iii)** Modify Image Contrast.  
      <img width="794" height="213" alt="WhatsApp Image 2026-05-11 at 2 05 39 PM" src="https://github.com/user-attachments/assets/286c13db-b1c3-4c0a-ad26-7326d572e60d" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

