# Tiny SSD Object Detection

  A small Single Shot MultiBox Detector (SSD) built from scratch in PyTorch (anchor boxes, IoU matching, offset regression, non-maximum suppression) and trained on the banana detection dataset.

  Based on the *Dive into Deep Learning* computer vision chapter (d2l 0.17.0).
A small Single Shot MultiBox Detector (SSD) built from scratch in PyTorch (anchor boxes, IoU matching, offset regression, non-maximum suppression) and trained on the banana detection dataset.

Based on the *Dive into Deep Learning* computer vision chapter (d2l 0.17.0).

## Notebooks

- `01-bounding-boxes`: box formats (corners / center)
- `02-anchor`: anchor generation, IoU, anchor labeling, NMS
- `03-multiscale-object-detection`: multiscale anchors
- `04-object-detection-dataset`: banana dataset loading
- `05-ssd`: Tiny SSD model, training, prediction

## Dataset

The [banana detection dataset](https://d2l.ai/chapter_computer-vision/object-detection-dataset.html) (1000 training and 100 validation images, 256×256, one banana per image) is downloaded automatically on first run.

## Running

Run `05-ssd` top to bottom, locally or on Google Colab (a GPU makes training much faster). No manual download is needed.

## Training

- Optimizer: SGD, lr 0.2, weight decay 5e-4
- Batch size: 32
- Epochs: 30
- Losses: cross-entropy (classes) + Smooth  L1 (box offsets)
- Hardware: Google Colab GPU

## Results

- AP@0.5: 0.983
- AP@0.75: 0.337
- AP@[.5:.95]: 0.453
- Parameters: 1.01 M
- Inference (Colab GPU): 8.4 ms / image (119 FPS)

The model finds almost every banana (AP@0.5 close to 1), but its boxes are not tight enough for stricter IoU thresholds (AP@0.75 = 0.34). Inference time covers the network only, without NMS.

## Requirements

Python 3, PyTorch, matplotlib, pandas, Pillow.
