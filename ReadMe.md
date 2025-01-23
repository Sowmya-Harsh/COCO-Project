# COCO Eye Tracking and Segmentation Project

## Overview
This project explores eye-tracking data in conjunction with the COCO (Common Objects in Context) dataset using Python. The primary goal is to analyze object segmentation and gaze points on images to derive insights into visual attention mechanisms. It involves downloading necessary COCO dataset files, processing annotations, drawing masks and gaze points on images, calculating average areas of objects, normalizing these areas, and performing advanced tasks such as analyzing the correlation between object size and attention.

## Authors
- Omkar Desai
- Sowmya Janmahanthi

## Prerequisites
To run this project, you need:
- Python 3.x installed.
- Jupyter Notebook or any other Python environment.
- Install the required libraries by running:
    ```bash
    pip install requests opencv-python-headless Pillow pandas matplotlib shapely
    ```

## Directory Structure
Ensure the following directory structure exists before running the script:
/c-team-coco/

├── annotations_trainval2017/

│ └── annotations/

├── val2017/



## Setup Instructions

### Downloading Required Data
The script contains functions to automatically download and unzip the necessary files:
- **COCO Dataset Annotations**: Run `download_and_unzip_annotations_file(url)` where `url` is `"http://images.cocodataset.org/annotations/annotations_trainval2017.zip"`.
- **COCO Dataset Validation Images**: Run `download_and_unzip_val2017_images_file(url)` where `url` is `"http://images.cocodataset.org/zips/val2017.zip"`.
- **COCOSearch18 Fixation Data**: Run `download_and_unzip_CocoSearch18_files(url)` where `url` is `"http://vision.cs.stonybrook.edu/~cvlab_download/COCOSearch18-fixations-TP.zip"`.

These functions will handle the downloading and extraction process, creating the directories mentioned above if they do not exist.

## General Tasks

### Task 1: Draw Masks on Images
- Function: `draw_mask_on_image(image: np.ndarray, mask: np.ndarray) -> np.ndarray`
- Description: Draws a polygon mask over an image based on the given segmentation data.
- Usage: 
    ```python
    testing_masking(annotation_index)
    ```
    This function tests the mask-drawing functionality on random images from the dataset.

### Task 2: Draw Gaze Points on Images
- Function: `draw_gaze_points_on_image(image: np.ndarray, gaze_points: np.ndarray) -> np.ndarray`
- Description: Draws gaze points on images, with the radius proportional to fixation duration.
- Usage: 
    ```python
    test_with_random_images_and_gaze_points()
    ```
    This function generates random gaze points on randomly selected images and displays them.

### Task 3: Calculate Average Area of Objects
- Function: `calculate_average_area_of_objects(objects: dict) -> pd.DataFrame`
- Description: Computes the average area occupied by each class of objects in the dataset.
- Usage: 
    ```python
    calculate_average_area_of_objects(coco_data)
    ```

### Task 4: Calculate Normalized Average Area of Objects
- Function: `calculate_average_normalized_area_of_objects(objects: dict) -> pd.DataFrame`
- Description: Calculates the normalized average area occupied by each class relative to the image dimensions.
- Usage: 
    ```python
    calculate_average_normalized_area_of_objects(coco_data)
    ```

## Advanced Tasks

### Advanced Task 1: Find the Most Attractive Class in the Dataset
- Function: `calculate_average_duration(coco_data, gaze_tracking_data)`
- Description: Analyzes the average fixation duration per object category to determine which categories attract more attention.
- Usage: 
    ```python
    result = calculate_average_duration(coco_data, eye_tracking_data)
    print(result)
    ```

### Advanced Task 2: Does Object Size Drive First Glance Attention?
- Function: `analyze_object_size_attention(coco_data, gaze_tracking_data)`
- Description: Investigates whether larger objects receive more initial attention compared to smaller ones.
- Usage: 
    ```python
    result = analyze_object_size_attention(coco_data, eye_tracking_data)
    for category, avg_size, prob in result:
        print(f"Category: {category}, Avg Size: {avg_size:.2f}, Probability: {prob:.2f}")
    ```

## Running the Script
1. Open the script in Jupyter Notebook or any other Python IDE.
2. Ensure all prerequisites are met.
3. Execute cells sequentially to perform the general and advanced tasks as described above.


## License
This project is licensed under the MIT License - see the LICENSE file for details.

├── Masked_images/

├── gazed_points_images/

└── COCOSearch18-fixations-TP/

