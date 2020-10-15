# HousePrices

This is an attempt on the Kaggle House prices competition. Attempts and results will be updated along the way as I progress on with this mini project.

## Files:
1) HousePrices_datacleaning.ipynb
  The jupyter notebook coded for cleaning train.csv and test.csv
  
2) Train_clean.csv and Test_clean.csv
  
- The csv files that have been cleaned using the .ipynb in 1). The catagorical variables are one hot encoded if they have no relation in magnitude, and coded in the sense of its importance/magnitude if there are. NaNs are filled with 0's as most of them refers to the variable being not present.

- One row has been removed from the original train.csv as there is a missing value for a variable.

3) HousePrices_datacleaning.ipynb
- The jupyter notebook with XGBoost method used.

## Updates

### 15th October, 2020

An attempt was done with the XGBRegressor with the default parameters and also doing hyperparameter tuning with HyperOpt. The results are as follows:

- XGBRegressor, default parameters:

Parameters: {base_score=0.5, booster='gbtree', colsample_bylevel=1,
             colsample_bynode=1, colsample_bytree=1, gamma=0, gpu_id=-1,
             importance_type='gain', interaction_constraints='',
             learning_rate=0.300000012, max_delta_step=0, max_depth=6,
             min_child_weight=1, missing=nan, monotone_constraints='()',
             n_estimators=100, n_jobs=0, num_parallel_tree=1, random_state=0,
             reg_alpha=0, reg_lambda=1, scale_pos_weight=1, subsample=1,
             tree_method='exact', validate_parameters=1, verbosity=None}
             
MAE: 16234.42

Ranking: 6634/49372, Top 13.4%

- XGBRegressor, hyperparameter tuning with HyperOpt

Parameters tuned: {'max_depth': hp.randint('max_depth', 20),
                  'gamma': hp.uniform ('gamma', 0,2),
                   'colsample_bytree' : hp.uniform('colsample_bytree', 0.001,1),
                  'n_estimators': hp.randint("n_estimators", 500),
                   'learning_rate': hp.uniform('learning_rate',0, 1),
                   'subsample': hp.uniform('subsample',0, 1),
                   'min_child_weight': hp.uniform('min_child_weight',0, 3),
                   'reg_lambda' : hp.uniform('reg_lambda', 0,2)
                   }
                   
MAE: 13877.53

Ranking: 1253/49372, Top 2.53%
