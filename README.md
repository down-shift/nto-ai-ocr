# Optical Character Recognition for NTO AI 2022 finals

This repository contains the code for recognition of handwritten text. The project was created for the finals of AI National Technological Olympiad in collaboration with [@zaborshikov](https://github.com/zaborshikov). The baseline was provided by Sber AI.

# Overview

First, we have to split the image into separate words, as shown on the example:

![](https://github.com/down-shift/nto-ai-ocr/blob/main/segm_sample.png)

Then, each word would be recognized by OCR algorithm:

![](https://github.com/down-shift/nto-ai-ocr/blob/main/ocr_sample.png)

# Segmentation

We used Mask-RCNN X101 32x8d FPN 3x Architecture from Detectron2 model zoo for instance segmentation. 
The performance was estimated by F1-score metrics. The evaluation result we got was 0.88.

# OCR

There are two OCR models in this repository:
- CRNN + CTC Loss + Resnet34 
- Transformer + DenseNet161 (credit to [@t0efL](https://github.com/t0efL) for model implementation)

Both models were trained on the dataset consisting of >100k word instances. After performance estimation, CRNN model was chosen.

# Files:
- segmentation.ipynb: Mask-RCNN model
- recognition.ipynb: CRNN model
- transformer.ipynb: Transformer model
- to_gray.ipynb: utility for converting images into grayscale and enhancing contrast
- ocr_model.ipynb: pipeline for Mask-RCNN and CRNN
