<img src="https://github.com/AdamAdonyi/QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure/blob/main/smiles.png"/>


# QSAR-Challenge-Predicting-Biological-Activity-from-Chemical-Structure
This project addresses the task of predicting a molecule's biological activity or toxicity based on its chemical structure. Using a Quantitative Structure-Activity Relationship (QSAR) approach, we aim to train a machine learning model capable of accurately classifying molecules as active, inactive, or unknown.



# Data:

The dataset consists of molecules represented in SMILES format, along with their corresponding activity labels of 11 separated category (+1: active, 0: unknown, -1: inactive). The data is super inbalanced but see more detail in the EDA

# Model:

I employed a Deep Learning Neural network models. The models were trained on a portion of the dataset and evaluated on a separate testing set.

# Evaluation:

The performance was assessed using the auc on the evaluation server, which calculates the mean Area Under the ROC Curve (AUC) while considering the presence of unknown labels.

# Results:

I reached 0.652 AUC which considered a good score in case of the unbalanced data

# Future Work:

It would be nice to improve the performance:
  - generating more data (Morgan Fingerprint)
  - introducing more QC step focusing on distributions of descriptions
  - testing optimizers and fine tune hyperparameter (gridsearch)
