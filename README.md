# Dementia Classifier using medical data

This project was made for *Introduction to Machine Learning* classes at Faculty of Mathematics and Information Sciences at Warsaw University of Technology.

## Authors

- [Jan Opala](https://github.com/opalaj)
- [Aleksandra Wójcik](https://github.com/WojcikAleksandra)

## Data used
The data comes from the dataset [Dementia Patient Health Dataset](https://www.kaggle.com/datasets/timothyadeyemi/dementia-patient-health-dataset).

## EDA and preprocessing
The dataset contains 24 variables and 1000 rows (unique patients). Most of them focused on health parametres (weight, body temperature, dosage of drugs for dementia), but there were present also columns related to more general aspects of life such as education level, dominant hand or gender.
In order to get rid of categorical variables we decided to map columns into dummy variables (depression status or gender, 1 for women) or add intermediate states (smoking status had 0.5 as intermediate) so that some gradation was visible. Type of diet, diseases and name of prescriped drugs became dummy variables.
Some interesting dependencies between data can be seen on crosstabs below:
![crpsstabs](https://github.com/JanOpala/dementia-classifier/blob/main/dementia_classifier_screenshots/crosstabs.png)

## Models overview
We decided to test the dataset on various models using original data and data reduced to 4 most significant columns (after PCA). For each model independent of the chosen dataframe the F1 score and other metrics received extemely high metrics, approximately 1. After such high scores we decided to investigate the explainability of the models and we found out that a variable of a 'cognitive test score' fully determine whether a patien has dementia or not (which is justified since the test is used for diagnosis).
![dominant](https://github.com/JanOpala/dementia-classifier/blob/main/dementia_classifier_screenshots/dominant_variable.png)
We decided to remove the dominant variable and to test models on the reduced dataframe so that it could be possible to predict dementia without the cognitive test for diagnosis. We obtained the best F1 score for the decision tree (0.767).
Variable importance for reduced  model for multi layer perceptron can be seen below:
![no dominant](https://github.com/JanOpala/dementia-classifier/blob/main/dementia_classifier_screenshots/no_dominant.png)
