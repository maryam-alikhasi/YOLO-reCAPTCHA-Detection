# YOLO-reCAPTCHA-Detection

This project implements an object detection pipeline using **YOLOv5** on the **Google reCAPTCHA Dataset** from Kaggle. The goal is to detect and classify common objects found in reCAPTCHA challenges using a pretrained YOLOv5 model.

---

## Dataset

- **Source**: [Kaggle - sanjeetsinghnaik/google-recaptcha](https://www.kaggle.com/datasets/sanjeetsinghnaik/google-recaptcha)
- **Description**: A set of images similar to those used in Google's reCAPTCHA systems, containing street signs, vehicles, traffic lights, etc.

---

## Model

- **Architecture**: YOLOv5 (small variant `yolov5s`)
- **Framework**: [Ultralytics YOLO](https://github.com/ultralytics/ultralytics)
- **Pretrained weights**: `yolov5s.pt` from Ultralytics

---

## Objective

1. Download the Google reCAPTCHA Dataset.
2. Use YOLOv5 to detect objects in a random selection of 5 images.
3. Save the visual results of detection with bounding boxes.
4. Display the detected object classes for each image.

---

## How to Run (on Google Colab)

1. Upload your `kaggle.json` (API token) to Colab.

```python
from google.colab import files
files.upload()
````

2. Download the dataset:

```python
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json

import kagglehub
path = kagglehub.dataset_download("sanjeetsinghnaik/google-recaptcha")
```

3. Install dependencies and load model:

```python
!pip install -q ultralytics
from ultralytics import YOLO

model = YOLO('yolov5s.pt')
```

4. Run detection on 5 random images and save the results.

---

## Notes

* This implementation uses **YOLOv5** with **pretrained weights**, so it might not perfectly match the target objects unless fine-tuned on reCAPTCHA.
* For production use, consider annotating a subset of the dataset and retraining/fine-tuning the model.
