# Tiny SSD Object Detection

A small Single Shot MultiBox Detector (SSD) built from scratch in PyTorch (anchor boxes, IoU matching, offset regression, non-maximum suppression) and trained on a custom single-class object detection dataset.

Based on the *Dive into Deep Learning* computer vision chapter (d2l 0.17.0).

## Notebooks

01-bounding-boxes: Box formats (corners / center)
02-anchor: Anchor generation, IoU, anchor labeling, NMS
03-multiscale-object-detection: Multiscale anchors
04-object-detection-dataset: Banana dataset loading
05-ssd: Tiny SSD model, training, prediction

## Dataset
The [banana detection dataset](https://d2l.ai/chapter_computer-vision/object-detection-dataset.html) (1000 training and 100 validation images, 256×256, one banana per image) is downloaded automatically on first run.

CSV format: `img_name,class_id,x1,x2,y1,y2` (pixels, 256×256 images, one object per image).

Differences from the banana loader in `05-ssd`:
- columns are reordered to `(class, x1, y1, x2, y2)` before normalization;
- zero-size boxes (annotation errors) are dropped and coordinates are clipped to the image.

## Running

Run `05-ssd` top to bottom, locally or on Google Colab (a GPU makes training much faster). No manual download is needed.
