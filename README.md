I have added three different model types from the ISIC 2024 cancer detection competition. The data can be found on Kaggle at https://www.kaggle.com/competitions/isic-2024-challenge. The data consists of separate image-data and tabular-data. The metric for performance is Partial AUC (PAUC) above .8 so a higher score is better with a maximum score of .20. The models are listed in order of private leaderboard performance based on this metric which is a blind measure of generalization of the models. 

Model 1 (PAUC .16098) uses only the tabular (no images) and is an ensemble of three different models: 1. lightgbm, 2. catboost, 3. xgboost. Each model was tuned using a parameter grid containing a range of possible parameter values. However, only the best parameter values were retained in the script. This model uses 7-fold cross-validation.

Model 2 (PAUC .13622) uses only tabular data and is just a random forest, tuned using GridSearchCV. This model uses 5-fold cross-validatation.

Model 3 (PAUC.12309) uses image and tabular data. This model uses RESNET18 to create features from images, the BERT large language model to create features from the metadata, then calculates logits from the combined features.   
