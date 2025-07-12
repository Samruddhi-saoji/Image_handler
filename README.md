# Image Processing Utilities

This repository is a personal collection of frequently used image processing functions built with OpenCV, NumPy, and Matplotlib. These utilities simplify basic and intermediate image manipulation tasks for both grayscale and color images.

---

## Features Covered

### Basics
- Read a grayscale or color image
- Save an image
- List all images in a folder
- Delete all files in a folder
- Display an image (grayscale)

### Colored Image Handling
- Read and save color images
- Pixel-level modifications (set pixel color, set specific channels)
- Color classification (check if pixel is red, blue, green, gray, white, or black)

### Other Functions
- Compress an image to a lower resolution
- Crop an image to a given region
- Create a composite image from a list of images (with optional weights)
- Convert `.tif`/`.tiff` to `.jpeg`
- Mark points (e.g., p1, p2, … pn) on grayscale images with colored dots

---

## Requirements

- Python 3.x  
- [OpenCV](https://opencv.org/) (`cv2`)  
- NumPy  
- Matplotlib  
- Pandas  
- glob  
- os  

Install with:

```bash
pip install opencv-python numpy matplotlib pandas
```

---

## 🔧 Usage

### Reading and Saving

```python
img = read("path/to/image.jpeg")
save(img, "output.jpeg")
```

### List and Delete Files

```python
# get all the images in a folder
images, names = list_images("src_folder")

# process the images, and save in destination folder
for i, img in enumerate(images):
    #process image
    process_img = process(img)

    # get dest path
    name = names[i]
    dest_path = os.path.join("dest_folder", name)

    # save processed image
    save(processed_img, dest_path)


delete_all_files("src_folder/")
```

### Display Image

```python
display(img)  # works for grayscale images
```

### Image Compression and Cropping

```python
# Reduce image from shape (r1, c1) to (r2, c2)
compressed = compress_img(img, r1=400, c1=750, r2=100, c2=188)
# done via pixel skipping

# crop 
cropped = crop(img, r_start=50, num_rows=200, c_start=100, num_cols=300)
```

### Composite Creation

```python
# get a weighted composite of three images
composite = get_composite([img1, img2, img3], weights=[1, 2, 1], sum_only=False)
```

### Pixel Operations (Color Images)

```python
img = set_pixel(img, (50, 100), (255, 0, 0))  # set to blue
if isRed(img[50, 100]):
    print("It's red!")
```


