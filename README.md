## I. Introduction
This project aims to find the best model to apply for minimizing fraudulent transactions and optimizing operating processes of business.
## II. Process
### 1. Read file csv
<img width="673" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/4d97c23a-0b07-4a0c-a14a-1f32b30bf94f">

### 2. Cleaning data
<img width="673" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/a288e7e5-ff25-4842-8ec0-c943a3f3f0ad">

#### Comment:
- Dataset have no missing values in 23 columns
- Target column 'is_fraud' is highly imbalanced (95.3%)
- Excluding the features have high cardinality like: trans_date_trans_time, first, last, trans_num, unix_time
- To optimize model, we just keep locational features related to card holder that have numeric type like: lat, long
- As heatmap, the features have high correlation with target column: amt, category
- The other features: [gender, dob, job] will be EDA to check the correlation with target column.
### 3. EDA
<img width="681" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/df4822b2-df67-4a20-a9cb-c3543bef4324">
<img width="680" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/a4f73c27-fae7-4e80-ba07-98e793398a48">
<img width="679" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/dda7d0df-2917-4326-bb6b-0bbcab89c51e">
<img width="676" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/270b27b0-b591-4dc9-aec4-599e9c0a7ac6">

#### Conclusion after EDA:
- cc_num: the primary key of dataset
- amt, category: they have high correlation with target column (following to Heatmap)
- lat, long: the location of card holder but in numeric type
- dob: year of birth of the card holder (keep dob values have % fraud > percentile 88)
- job: the job of card holder (keep job values have % fraud > percentile 95)
### 4. Encoding the categorial data into numerics
<img width="677" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/ec6f5e2b-6a59-4c3b-a60a-fa25f00880d3">

### 5. Scaling/Normalization
<img width="680" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/13b350d7-c79b-4958-9b00-f80bd8da571f">

### 6.Apply Model
- Split train & test dataset
<img width="676" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/900a98df-2732-4a73-b3e6-621fb7b25ea7">

- Logistic Regression
<img width="679" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/24ef521b-3dae-424f-ae3e-359a91c5a673">

- Decision Tree
<img width="675" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/9f55f399-f161-4324-9251-86067cc403bf">
<img width="614" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/2fb8c59b-35a6-4eb1-aa77-cd0ba6bf1593">

- Random Forest
<img width="681" alt="image" src="https://github.com/mvqnhu/Fraud-Transaction-Model/assets/138433845/408aef64-9132-4ae3-b5a7-8d57d6583126">

## III. Conclusion
The balacen accuracy:
- Logistic Regression: 0.49 but F1-score = 0 ==> Dont choose this model
- Decision Tree: 0.54 and seems to be overfitting because F1-score of train dataset is bigger than F1-score of Test dataset
- Random Forest: 0.5
==>> We can consider to choose Decision Tree or Random Forest that is the best choice.
