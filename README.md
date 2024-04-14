# Retinal vessel segmentation via Deep Learning

![Retinal_Images](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/9c53d40e-9f4e-41b7-b4fe-422d1d724f10)

## Table of Content
- [Overview](#Overview)
- [Files](#Files)
- - [Jupyter Notebook](#Jupyter_Notebook)
- - [Dataset](#Dataset)
- [Model](#Model)
- [Evaluation](#Evaluation)
- [Results](#Results)

## Overview
This project focuses on the field of retina image processing, a crucial area in medical imaging and computer vision. The human retina plays a vital role in visual perception, and analyzing retinal images can provide valuable insights into various ocular diseases and conditions.

Retina image processing involves the application of advanced computational techniques, including deep learning to extract meaningful information from retinal images. By analyzing these images, healthcare professionals can detect abnormalities, track disease progression, and make informed decisions for diagnosis and treatment.

The goal of this project is to develop and showcase deep learning models and techniques for retinal image segmentation processing. By leveraging state-of-the-art neural networks and image processing methodologies, we aim to enhance the accuracy and efficiency of diagnosing retinal diseases, such as diabetic retinopathy, age-related macular degeneration, and glaucoma.

## Files
### Jupyter_Notebook
- ```Retina_Images_Processing.ipynb```: Juypyter Notebook containing all the code in preprocessing the retina images and building the model
(HTML file: ```Retina_Images_Processing.html``` is also available)

### Dataset
- ```retina_vessel_dataset.npz```: contains 610 raw retinal vessel images and labels in 2D (64x64)
  - **x_train**: 537 retinal vessel images for training, shape: (537, 64, 64)
  - **x_val**: 173 retinal vessel images for validation, shape: (173, 64, 64)
  - **y_train**: 537 labels for the training data, shape: (537, 64, 64)
  - **y_val**: 173 labels for the validation data, shape: (173, 64, 64)
  - **x_test**: 174 retinal vessel images for testing, shape: (174, 64, 64)
Below are some training samples and labels:
![Retinal_vessel_Sample_Training](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/1c6c980b-6ba6-4f16-a004-15b7ab0a84f5)
![Retinal_vessel_Sample_Training_2](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/4e17bdb6-7d00-438c-855c-3d66f7976a50)


  **y_test will not be available due to privacy issues** 

- ```sample_data.npz```: contains 2 retinal vessel images for visualizing and testing
  - **sample_img**: First retinal vessel image for testing, shape: (64, 64)
  - **sample_label**: **sample_img** after passing the **ideal** thershold, shape: (64, 64)
  - **sample_pred_soft**: blurred **sample_img**, shape: (64, 64)
  - **sample_pred_hard**: **sample_img** after passing the **expected (real)** thershold, shape: (64, 64)
  - **sample_raw**: Second retinal vessel image for testing, shape: (64, 64)
  - **sample_enhanced**: **sample_raw** after contrast stretching, shape: (64, 64)
  
  **Remark**
  - NPZ files is a compressed archive format used by NumPy to store arrays and other data.
  -  After passing the thershold, all the pixel values are 1 or 0

## Model
 The model is autoencoder, a special type of convolutional neural network.
### Convolutional Neural Network (CNN)
![CNN](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/d0e15eab-f15d-4470-81dd-e8a90c0bac92)
For the CNN image classification model, Image undergoes an "abstraction" path that reduces the spatial dimension of the input via pooling operations while increasing the number of channels with convolution layers along the path. The compressed feature resulting from the abstraction path subsequently gets flattened, from which a set of dense layers further manipulates the flattened features to yield the final classification prediction.

### Autoencoder
![Autoencoder](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/8dadee0a-2099-42bf-ad62-3bbe68f7d353)
Autoencoder, or an "hourglass" model, is a simple extension of the previously mentioned image classification model. The process of obtaining the compressed feature shares the same concept of abstraction path introduced in the classification model. The compressed feature is then propagated to the expansion path, which de-compresses the compressed feature back to the spatial representation of the image. In this arrangement, the compressed feature is often called the "Bottleneck" feature.

We will use this autoencoder architecture to build a model that can learn to produce a segmentation mask from the input image. Intuitively, we expect the output of the autoencoder to be the predicted segmentation mask. During training, the loss will be computed between the real label mask and the predicted mask.

## Evaluation
We will use a evaluation metric called the Dice coefficient, one the most dominantly used metrics for segmentation tasks.
![Dice_Coefficient](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/5ba0a5c5-a682-4a0d-abbc-e3feaeb14fad)

The dice coefficient measures the similarity between two segmentation masks by comparing pixel-wise agreement. It is computed as twice the area of overlap divided by the sum of the areas of both masks. If two masks are identical, the Dice coefficient will give the highest value of 1, and if the two masks have no overlap at all, then it will give the lowest value of 0.

## Results
### Predicted Segmentation
![Results_Before_Thershold](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/e6e335fa-6d2a-451f-925e-324ecf77093a)

Since the predicted segmentation is blurred, we need to add a thershold.
![Results_After_Thershold](https://github.com/Cheung-Chak-Hang-Billy/Retina-Images-Processing/assets/148378750/5de345d5-f7be-4ebb-a6d9-2de545063419)

At last, our model gives  0.7448 dice coefficient on the validation set.

<p align="right">(<a href="## Table of Content">back to top</a>)</p>

## Contact

## Acknowledgement
