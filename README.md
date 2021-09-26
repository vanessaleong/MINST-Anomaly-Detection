# MINST Anomaly Detection
Identify anomaly in the popular MINST handwritten dataset where digit 0 is labelled as normal while digits 1-9 are labelled as anomaly.  
This project serves as a discovery and comparison across different deep learning & CNN architectures and its impact on the results.

## Feature Engineer & Modelling 
With over 6000 MINST labelled images, data augmentation (rotation, zooming, adding noise) was done to expand upon the training data for robustness and better generalisation.

Two main models were explored: **Autoencoder** and **Convolutional Neural Network (CNN)**
1. **Autoencoder** was used for 2 purposes - Classifier & Determine Reconstruction Errors
  * Classifier: with a fully connected layer for binary classification
  * Reconstruction Errors: training only on normal data, normal images will have small reconstruction error rate, while anomaly images will have high error rate

2. **CNN** was used as a Binary Classifier

To accurately evaluate an architecture's performance, a model is run 3 times with different weights initialized. They are then individually evaluated on the Test Dataset with AUC-ROC score averaged across the 3 iterations to determine the overall performance of the architecture. 

## Results
Possible explanation for the test result observed in the table below can be found in the PDF attached.
Ideally, parameter optimization could have been done, however, due to hardware constraints it was omitted from this experimentation.

1. **Autoencoder** Results 

| Model | Description | Avg. AUC Test Data |
| --- | --- | --- |
| 1 | Shallow Autoencoder | 0.99905 | 
| 2 | Shallow Autoencoder w L1 Regularization | 0.99901 | 
| 3 | Deep Autoencoder | 0.96879 | 
| 4 | Denoising Autoencoder | 0.99515 | 
| 5 | Six Conv(3x3) Max Pooling Autoencoder | 0.99329 | 
| 6 | Six Conv(5x5) Learnable Pooling Autoencoder | 0.98701 |
| 7 | Six Stacked(3x3) Learnable Pooling Autoencoder | 0.99640 |

2. **CNN** Results 

| Model | Description | Avg. AUC Test Data |
| --- | --- | --- |
| 1 | Two Conv(5x5) Max Pooling Pairs | 0.99085 | 
| 2 | Two Stacked(5x5) Conv-Max Pooling | 0.99304 | 
| 3 | Two Stacked(3x3) Conv-Max Pooling | 0.99486 | 
| 4 | Two Stacked(3x3) Conv-Learnable Pooling | 0.98809 | 
| 5 | Two Stacked(3x3) Conv-Learnable Pooling + Batch Norm | 0.99267 | 


