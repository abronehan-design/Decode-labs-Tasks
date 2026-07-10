# Project 2 - Automated Quality Inspection (Computer Vision)

## Overview

This project implements a computer vision pipeline that inspects gears on a conveyor belt and classifies them as **PASS** or **FAIL** by detecting broken teeth and cracks using OpenCV.

## Project Structure

```text
project2/
├── README.md
├── requirements.txt
├── generate_test_images.py
├── gear_inspection.py
├── test_images/
└── output/
```

## Implementation

### Dataset

`generate_test_images.py` creates a synthetic dataset containing 10 gear images (5 normal and 5 defective). Any real gear images can also be placed in the `test_images/` directory for inspection.

### Processing Pipeline

#### Image Preprocessing

Each image is converted to grayscale, blurred to reduce noise, and thresholded to obtain a binary image.

#### Defect Detection

Contours and convex hulls are extracted to identify convexity defects. Defects deeper than a predefined threshold are classified as structural defects.

#### Inspection

Each gear is labeled as **PASS** or **FAIL**. The detected defects are highlighted, and the annotated image is saved to the `output/` directory.

## Running the Project

```bash
pip install opencv-python numpy

python generate_test_images.py
python gear_inspection.py
```

## Configuration

| File                           | Description                                                   |
| ------------------------------ | ------------------------------------------------------------- |
| `generate_test_images.py`      | Generates the test dataset                                    |
| `gear_inspection.py`           | Image processing and defect detection pipeline                |
| `THRESHOLD_VALUE`              | Binary threshold for image segmentation                       |
| `DEFECT_DISTANCE_THRESHOLD_PX` | Minimum defect depth required to classify a gear as defective |

## Output

* PASS/FAIL result for each image
* Defect location and depth (if detected)
* Annotated inspection images saved in `output/`
* Overall inspection accuracy

## Deliverables

* `gear_inspection.py`
* `generate_test_images.py`
* Sample output images (PASS and FAIL)
* Final inspection accuracy and a brief explanation of the selected defect threshold
