# Part 6: Give it your best shot!

## Model 1: Decision Tree
[Comet.ml](https://www.comet.com/hfereidouni/ift6758/d05a70aa1cda41c199402e7f595f8e49?experiment-tab=panels&showOutliers=true&smoothing=0&xAxis=wall)
#### First we have load our code with all features from part 4, then like in Part 5 we have applied one-hot encoding for String features.
### Step 1: Data Pre-processing
1. Drop `change_shot_angle` column where the majority of datas are NaN, then drop NaN values.
2. Using Variance filter method to filter low variance features using `VarianceThreshold`
### Step 2: Hyperparameters tuning
Hyperparameters to tune:
```'class_weight':[{0:1,1:1},{0:3,1:1},{0:6,1:1},{0:12,1:1},{0:50,1:1},{0:100,1:1},{0:1000,1:1}],
    'criterion':['gini','entropy'],
    'max_depth':[1,5,10,15,20,40],
    'min_samples_split':[2,8,16,32,64],
    'min_samples_leaf':[1,2,4,16,32,64]
```
As we can see there are lots of possible combinations, so we have chosen **Randomized Search** to optimize our Algorithme.
### Step 3: Feature selection
After applying wrapper method and optimizing algorithm, we apply a Wrapper method(RFE) to then reduce the half of the features to 6.

### Model
After all these processes, we have trained a Decision Tree model using the tuned hyperparameters and selected features.
Comparing to a non-tuned Decision Tree that is trained with all datas, the tuned model has a better performance in terms of roc auc score.
### ROC AUC Compare
![ROC_AUC_compare](./images/part%206/ROC_dt_compare.png)
### ROC AUC figure
![ROC_AUC](./images/part%206/ROC_dt_fine.png)
### Goal Rate vs Shot probability percentile
![Goal_rate](./images/part%206/../part%206/goal_rate_dt_fine.png)
### Cumulative % of Goals vs Shot probability percentile
![Cumulative sum](./images/part%206/cumulative_dt_fine.png)
### Calibration Curve
![Cali plot](./images/part%206/cali_plot_dt_fine.png)



## Model 2: Random Forest
[Comet.ml](https://www.comet.com/hfereidouni/ift6758/f1acaef6a6da4aff8a348a1e73da40eb?experiment-tab=panels&showOutliers=true&smoothing=0&xAxis=step)
#### First we have load our code with all features from part 4, then like in Part 5 we have applied one-hot encoding for String features.
### Step 1: Data Pre-processing
1. Drop rows where NaN values are found. 
### Step 2: Hyperparameters tuning
We have used the following hyper-paramter-value pairs instead of tuning the Hyperparameters:
```
    n_estimators=200,
    random_state=42,
    class_weight="balanced", 
```
Note that we have used ***class_weight*** so that the random forest model accounts for the class imbalance present in the dataset.
### Step 3: Feature selection
Using SelectKBest method along with mutual_info_classifi to filter K best features using 'Mutual Information' with Label/Class as a hueristic. We used the alue of k=10, which means we selected best 10 feeatures based on Mutual information with label.

### Model
After all these processes, we have trained a Random Forest model using the above hyperparameters and selected features.
### ROC AUC figure
![ROC_AUC](./images/part%206/Random_Forest_KBest_MI_ROC_KBest_MI_random_forest_no_tuning.png)
### Goal Rate vs Shot probability percentile
![Goal_rate](./images/part%206/Random_Forest_KBest_MI_goalratepercentile_KBest_MI_random_forest_no_tuning.png)
### Cumulative % of Goals vs Shot probability percentile
![Cumulative sum](./images/part%206/Random_Forest_KBest_MI_cumulativegoalrate_KBest_MI_random_forest_no_tuning.png)
### Calibration Curve
![Cali plot](./images/part%206/Random_Forest_KBest_MI_calibration_KBest_MI_random_forest_no_tuning.png)

## Model 3: Logistic Regression with L1 regulizer

### Step 1: Hyperparameters tuning
Based on our implementation of logistic regression in part 3, we did some hyperparameter tuning and added L1 regulizer as an added optimizer in this part.

### Step 2: Feature selection
For this part we have selected fetaures ['game_time','period','x','y','shot_type','last_event_type', 'x_coord_last_event', 'y_coord_last_event', 'Time_from_the_last_event', 'Distance_from_the_last_event', 'Rebound', 'change_shot_angle', 'Speed', 'shot_dist','angle_net'] to train our model.

### Model
After all these processes, we have trained a Logistic Regression model using the above hyperparameters and selected features.

### ROC Curve
![ROC Curve](./images/part%206/Log_Reg_L1_i4.png)

### Goal Rate
![Goal Rate](./images/part%206/Log_Reg_L1_i3.png)

### Cumulative % of goals
![Cumulative % of goals](./images/part%206/Log_Reg_L1_i2.png)

### Reliability Curve
![Reliability Curve](./images/part%206/Log_Reg_L1_i1.png)


## Model 3: Logistic Regression with L1 regulizer
[Comet.ml](https://www.comet.com/hfereidouni/ift6758/e80d146da5774672afde1533415d4544?experiment-tab=panels&showOutliers=true&smoothing=0&xAxis=step)
### Step 1: Hyperparameters tuning
Based on our implementation of logistic regression in part 3, we did some hyperparameter tuning and added L1 regulizer as an added optimizer in this part.

### Step 2: Feature selection
For this part we have selected fetaures ['game_time','period','x','y','shot_type','last_event_type', 'x_coord_last_event', 'y_coord_last_event', 'Time_from_the_last_event', 'Distance_from_the_last_event', 'Rebound', 'change_shot_angle', 'Speed', 'shot_dist','angle_net'] to train our model.

### Model
After all these processes, we have trained a Logistic Regression model using the above hyperparameters and selected features.
### ROC Curve
![ROC Curve](./images/part%206/Log_Reg_L1_i4.png)
### Goal Rate
![Goal Rate](./images/part%206/Log_Reg_L1_i3.png)
### Cumulative % of goals
![Cumulative % of goals](./images/part%206/Log_Reg_L1_i2.png)
### Reliability Curve
![Reliability Curve](./images/part%206/Log_Reg_L1_i1.png)
### Best Models:

### ROC AUC Comparison
![ROC_AUC_compare](./images/part%206/ROC_dt_fine.png )|![ROC_AUC](./images/part%206/Random_Forest_KBest_MI_ROC_KBest_MI_random_forest_no_tuning.png)|![ROC Curve](./images/part%206/Log_Reg_L1_i4.png) \
By comparing the roc_auc score of the two models: The Decision tree has a slightly better performance than Random Forest.

### Calibration Comparison
![Cali plot](./images/part%206/cali_plot_dt_fine.png)|![Cali plot](./images/part%206/Random_Forest_KBest_MI_calibration_KBest_MI_random_forest_no_tuning.png)|![Reliability Curve](./images/part%206/Log_Reg_L1_i1.png) \
When it comes to reliability curve, Random Forest has a better curve that is more close to the perfectly calibrated line.

### Precision and recall
#### Decision Tree
- precision: 0.229
- recall: 0.002
#### Random Forest
- precision: 0.0359
- recall: 0.0642165342748
#### Logistic Regression
- precision: 0.184
- recall: 0.70

Here we have decided to use **Random Forest** as out best model after comparison:
- Its reliability curve is closer to the perfect classfier one
- Its Precision and recall are more reasonable compared to Decision Tree and Logistic Regression
- Although the AUC-ROC is not as good as the others, but they are very close