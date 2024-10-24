# AI-in-Pathology-Image-Analysis

This repository contains the coursework assignment for the MSc Cancer Genomics and Data Science program. The task involves analyzing pathology images using Convolutional Neural Networks (CNNs).  

### Project Overview  

The dataset consists of 8 Hematoxylin and Eosin (H&E) stained image files, labeled from A1 to D2, grouped into two distinct sets for building two CNN models:  

Group A: A1, A2 (for Model 1)  
Group B: B1, B2 (for Model 1)  
Group C: C1, C2 (for Model 2)  
Group D: D1, D2 (for Model 2)  


### Task Summary  

1) Pre-process the images: Divide them into patches of size 100 x 100 pixels.  
2) Generate train and test sets: Split the data into 90% training and 10% testing.  
3) Build two CNN models:  
   • Model 1 for differentiating between Groups A and B.  
   • Model 2 for differentiating between Groups C and D.  
4) Evaluate performance: Test each model's accuracy and assess overfitting and generalization issues.  


### Project Workflow  

1) Image Pre-processing  
   • Images are processed into smaller patches of 100 x 100 pixels to facilitate training on localized features.  
2) Train-Test Split  
   • The dataset is split into a 90:10 ratio for training and testing purposes.  
       Model 1: Train on Groups A1, A2, B1, and B2.    
       Model 2: Train on Groups C1, C2, D1, and D2.  
3) Building CNN Models
   • Model 1: Classifying Group A vs. Group B.
   • Model 2: Classifying Group C vs. Group D.
4) Model Testing
  • Both models are evaluated for training accuracy, validation accuracy, and test performance.  
  

### Results  
  
Model 1 Performance (Group A vs. Group B):  
• Training Accuracy: 85.45%  
• Validation Accuracy: 80.00%  
Model 2 Performance (Group C vs. Group D):  
• Training Accuracy: 89.61%  
• Validation Accuracy: 69.99%  
  
### Post-Analysis Discussion  
  
**Which Model Performed Better?**  

At first glance, Model 1 appears to outperform Model 2 based on the validation accuracy. However, upon closer inspection, both models demonstrate a tendency to predict the majority class in the test sets:  
  
• Model 1 predicted mostly Group B (Test set ratio: 8 B, 2 A).  
• Model 2 predicted mostly Group D (Test set ratio: 7 D, 3 C).  
  
This suggests that both models are overfitting the training data and are not learning meaningful distinctions between the classes. The test accuracy fluctuates based on the class distribution, indicating that the models are biased toward the majority class.  
  
Several strategies were employed to address the overfitting issue:

Reduced model complexity: Simplified model architectures.
Regularization techniques: Added dropout layers and applied kernel and bias regularization to promote generalization.
Despite these efforts, the models continued to overfit the training data, likely due to the sparsity of the dataset. More data is needed to improve the models' robustness and ability to generalize well.












Instructions - process the images into patches of 100 by 100. Then, generate the train and test set using 90:10 ratio. Build 2 CNN models for each images pair. 

**Image pre-processing**
**Preparing the train test split for model 1 and model 2**
**Building 2 CNN models to predict 1) A vs B and 2) C vs D**
**Testing moodel 1 and model 2**


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
