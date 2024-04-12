# Retina Images Processing Using Deep Learning

![Retinal_Images](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/9c53d40e-9f4e-41b7-b4fe-422d1d724f10)

## Table of Content
- [Overview](#Overview)

## Overview
This project focuses on the field of retina image processing, a crucial area in medical imaging and computer vision. The human retina plays a vital role in visual perception, and analyzing retinal images can provide valuable insights into various ocular diseases and conditions.

Retina image processing involves the application of advanced computational techniques, including deep learning to extract meaningful information from retinal images. By analyzing these images, healthcare professionals can detect abnormalities, track disease progression, and make informed decisions for diagnosis and treatment.

The goal of this project is to develop and showcase deep learning models and techniques for retinal image segmentation processing. By leveraging state-of-the-art neural networks and image processing methodologies, we aim to enhance the accuracy and efficiency of diagnosing retinal diseases, such as diabetic retinopathy, age-related macular degeneration, and glaucoma.

## Files
### Jupyter Notebook
- ```Retina_Images_Processing.ipynb```: Juypyter Notebook containing all the code in preprocessing the retina images and building the model
(HTML file: ```Retina_Images_Processing.html``` is also available)

### Dataset
- ```retina_vessel_dataset.npz```: contains 610 raw retinal vessel images and labels in 2D (64x64)
  - x_train: 537 retinal vessel images for training, shape: (537, 64, 64)
  - x_val: 173 retinal vessel images for validation, shape: (173, 64, 64)
  - y_train: 537 labels for the training data, shape: (537, 64, 64)
  - y_val: 173 labels for the validation data, shape: (173, 64, 64)
  - x_test: 174 retinal vessel images for testing, shape: (174, 64, 64)
  
  **y_test will not be available due to privacy issues** 

- ```sample_data.npz```:
  - sample_img: retinal vessel image for testing the dice coefficient, shape: (64, 64)
  - sample_label: label for sample_img, shape: (64, 64)
  - sample_pred_soft: 
  - sample_pred_hard:
  - sample_raw: 
  - sample_enhanced:
  
  **Remarks: NPZ files is a compressed archive format used by NumPy to store arrays and other data.**
