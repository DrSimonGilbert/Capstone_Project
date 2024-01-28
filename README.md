# Capstone_Project
Capstone Project Submission for Imperial College Certificate in Machine Learning and AI 2024 01

# PROJECT TITLE 
Identifying Human Vasculature in 3d Hierarchical Phase-Contrast Tomography (HiP-CT) data from human kidneys.

## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
Currently researches need to annotate human organ CT scan images by hand to identify blood vessels. This can take many months. A convolutional neural network may speed up this process, rapidly increasing the information available for researchers aiming to improving health and treat disease.

## DATA
The data is CT scans of human kidneys from deceased donors with accompanying maps to represent the blood vessels. The SenNet research group and Human Organ Atlas https://human-organ-atlas.esrf.eu/help provided the data as part of a Kaggle competition in November 2023 https://www.kaggle.com/competitions/blood-vessel-segmentation.   

## MODEL 
The model is a convolutional neural network (CNN) based on LeNet by LeCun et al and work done since then. These types of CNNs are good at interpreting images and are based on studying human vision.

Load the model in Python using joblib and pytorch:
Replace model_path in Training and Model Assessment.ipnb with 'model_lr_0.0024435642230605137_momentum_0.9521176292803581_dropout_0.6827284555071912_batch_21.pkl'

loaded_model = joblib.load(model_path)


## HYPERPARAMETER OPTIMSATION
I have used the Optuna optimisation package for Python with PyTorch with the following commonly selected hyperparameters:
learning rate; momentum; dropout rate, batch size. 

Replace study_path in Training and Model Assessment.ipnb with 'optuna_study_oversampling.pkl'

## RESULTS
The model was evaluated using accuracy metric on other non overlapping Chunks in the Test set.
Best study and chosed model had the following parameters:
Value: 88.43537414965986
 Params: 
    learning_rate: 0.0024435642230605137
    momentum: 0.9521176292803581
    dropout_rate: 0.6827284555071912
    batch_size: 21
    
![Running Best Accuracy](RunningBestAccuracy.png)


## (OPTIONAL: CONTACT DETAILS)
Dr Simon Gilbert MBBS BSC MRCGP
github_contact@drgilbert.co.uk

