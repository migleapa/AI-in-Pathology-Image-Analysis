# AI-in-Pathology-Image-Analysis

This repository contains the coursework assignment for the MSc Cancer Genomics and Data Science program. The task involves analyzing pathology images using Convolutional Neural Networks (CNNs).

8 H&E files provided starting with letters A-D. This is grouped as bellow:
• Group A: A1, A2 (For Model 1)
• Group B: B1, B2 (For Model 1)
• Group C: C1, C2 (For Model 2)
• Group D: D1, D2 (For Model 2)


Instructions - process the images into patches of 100 by 100. Then, generate the train and test set using 90:10 ratio. Build 2 CNN models for each images pair. 

## Image pre-processing
## Preparing the train test split for model 1 and model 2
## Building 2 CNN models to predict 1) A vs B and 2) C vs D
## Testing moodel 1 and model 2 


Post-analysis questions:

### What is the training and validation accuracy for model 1?
Model 1 - training accuracy: 0.8545, validation accuracy: 0.8000

### What is the training and validation accuracy for model 2?
Model 2 - training accuracy: 0.8961, validation accuracy: 0.6999

### Which of the models performed best on its dataset and suggest possible reasons for the differences in performance.

From the first glance it would seem that model 1 is performing better over model 2, but actually what
both models are doing, they always predict the majority class (Model 1 test set: B - 8, A - 2; model 2 test
data: D - 7, C-3). Multiple attemps were made where I generated different ratios of the classes in test set
to test this assumption - as the ratios change, the test accuracy would change accordinlgy, supporting
this assumption. This indicates that the model overfits training data and simply predicts the majority
class. I have performned many different experiments with multiple different model architectures where I
significantly dropped the model complexity as well as in some instances I introduced multiple dropout
layers to reduce the bias, or introduced generalization (kernel_regularizer and bias_regularizer) to help
model generalise better. Even after many different solutions, models would still overfit the training data.
These models simply do not work as the data is extremely sparse and both models don't have enough
data to learn the features well and generalise. More data are needed to make models more robust and
accurate. The other options could be to implement transfer learning.
