<img src="https://github.com/AdamAdonyi/QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure/blob/main/smiles.png"/>


# QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure
This project addresses the task of predicting a molecule's biological activity or toxicity based on its chemical structure. Using a Quantitative Structure-Activity Relationship (QSAR) approach, we aim to train a machine learning model capable of accurately classifying molecules as active, inactive, or unknown.



# Data:

The dataset consists of molecules (12 000) represented in SMILES format, along with their corresponding activity labels of 11 separated category (+1: active, 0: unknown, -1: inactive). The data is super inbalanced but see more details in the EDA. Test set has 5896 SMILES without labels in all 11 categories to evaluate the model. Challenge host provided server evaluating the model based on calculated AUC for prediction of the test set.

Data preparation had 3 pillars: Morgan Fingerprint (1024 added features), MACCSKeys (167 newly generated features), RDKit Desc. (210 new features) based on the SMILES.



<img src="https://github.com/AdamAdonyi/QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure/blob/main/strategy_data_prep.JPG">



# Generated training data: (12000x1385)


<img src="https://github.com/AdamAdonyi/QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure/blob/main/Heatmap_training_data.JPG">

# Model:

I employed Deep Learning Neural network models. The models were trained on a portion of the dataset and evaluated on a separate testing set.
Since the dataset was inbalanced, I created a model separately for each task. Each task-specific-model has a unique, distribution-specified class_weight assigned. 
The models have 6 layers with [ReLu](https://pytorch.org/docs/stable/generated/torch.nn.ReLU.html#relu) as activation function and  with instituted drop out layers (0.2). As Final output layer with 3 neurons, the activation was [softmax](https://pytorch.org/docs/stable/generated/torch.nn.Softmax.html). The used loss functin was [CategoricalCrossentropy](https://www.tensorflow.org/api_docs/python/tf/keras/losses/CategoricalCrossentropy), the optimizer was [Adamax](https://keras.io/api/optimizers/adamax/) with 0.001 learning rate and 0.9 momentum. Early stopping was tested (code sometimes contains it) but not used since I used 35 epochs with 32 batch size.
<img src= "https://github.com/AdamAdonyi/QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure/blob/main/model.png">



# Evaluation:

The performance was assessed using the auc on the evaluation server, which calculates the mean Area Under the ROC Curve (AUC) while considering the presence of unknown labels. During the training I modified hyperparameters based on the measured loss, accuracy, recall and F1 score.

# Results:

I reached 0.752 AUC which considered a good score in case of the unbalanced data

# Future Work:

It would be nice to improve the performance:
  - generating more data (Morgan Fingerprint)
  - introducing more QC step focusing on distributions of descriptions
  - testing optimizers and fine tune hyperparameter (gridsearch)
