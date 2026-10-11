# Tiny SSD Object Detection

A small Single Shot MultiBox Detector (SSD) built from scratch in PyTorch (anchor boxes, IoU matching, offset regression, non-maximum suppression) and trained on the banana detection dataset.

Based on the *Dive into Deep Learning* computer vision chapter (d2l 0.17.0), through the DLIM 2024 Lab 04 (Detection) course material.

## Notebooks

- `00-intro`: setup and GPU check
- `01-bounding-boxes`: box formats (corners / center)
- `02-anchor`: anchor generation, IoU, anchor labeling, NMS
- `03-multiscale-object-detection`: multiscale anchors
- `04-object-detection-dataset`: banana dataset loading
- `05-ssd`: Tiny SSD model, training, prediction

## Dataset

The [banana detection dataset](https://d2l.ai/chapter_computer-vision/object-detection-dataset.html) (1000 training and 100 validation images, 256×256, one banana per image) is downloaded automatically on first run.

## Running

Run `00-intro` to check the setup, then `05-ssd` top to bottom, locally or on Google Colab (a GPU makes training much faster). No manual download is needed.

Local install: PyTorch, then `pip install matplotlib numpy pandas pillow ipykernel`.

## Training

- Optimizer: SGD, lr 0.2, weight decay 5e-4
- Batch size: 32
- Epochs: 20
- Losses: cross-entropy (classes) + L1 (box offsets)
- Hardware: Google Colab GPU

## Results

Banana validation set (100 images), COCO-style evaluation (101-point interpolated AP, all detections after NMS):

- AP@0.5: 0.983
- AP@0.75: 0.337
- AP@[.5:.95]: 0.453
- Parameters: 1.01 M
- Inference (Colab GPU): 8.4 ms / image (119 FPS)

The model finds almost every banana (AP@0.5 close to 1), but its boxes are not tight enough for stricter IoU thresholds (AP@0.75 = 0.34). Inference time covers the network only, without NMS.

## Credits and license

- [Dive into Deep Learning](https://d2l.ai) by Aston Zhang, Zachary C. Lipton, Mu Li and Alexander J. Smola (text: CC BY-SA 4.0, code: MIT / MIT-0).
- DLIM 2024 Lab 04 course notebooks, derived from d2l.

This work is licensed under the [Creative Commons BY-SA 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).
