# DonorsChoose
##### kaggle problem : Data Science for Good: DonorsChoose.org

## Problem Statement
DonorsChoose.org has funded over 1.1 million classroom requests through the support of 3 million donors, the majority of whom were making their first-ever donation to a public school. If DonorsChoose.org can motivate even a fraction of those donors to make another donation, that could have a huge impact on the number of classroom requests fulfilled.
A good solution will enable DonorsChoose.org to build targeted email campaigns recommending specific classroom requests to prior donors. Part of the challenge is to assess the needs of the organization, uncover insights from the data available, and build the right solution for this problem.

>1. Goal: Predict weather the project submited will be approved or not, 1-approved 0-not approved
>2. Type: Binary Classification
>3. Metrics: AUC score, Confusion

### Few points About Dataset
* Project.csv
*-Contains 15 features regarding project details 
*- The values of feild  project_essay_3 & project_essay_4 are NAN for date after 2016-05-17 
-* There are missing values for many fields.
-* Dataset is highly imbalance.class 1 :#of sample 92706  & class  0 : #of sample 16542
* Resource.csv 
*-  Contains  details about resources neede for each project (3 features)
-*  No missing values 

### Data Analysis 
The analysis of data shows that classes can be seperated upto somewhat good extent one of reasons is high-imbalance

### Preprocessing 
Most features are text based only few are numeric i.e quantity, price & no_of_proj_previously_posted
So following text preprocessing steps performed in preprocesing 1.ipynb
*  Removed Non-alpha numeric characters except space
*  Lower case transformation
*  Removed stop words. Public dictionary used
*  Applied some filters i.e wouldn't -> would not similar kind
*  Performed lemitization by using parts of speech

and preprocessing 2.ipynb finds the 300 vector representation for the words that are revelent/ present in our dataset corpus and saves it as pickel file.

## Models and Training 
Right now there are 4 Models and every model have been used with multiple defferent feature sets.
### Naive Bayes
1. All text feature as one field + Column normalization of all feature (Name- set1)
2. All text feature as one field + Column normalization of originally numerical  feature only (Name- set2)
3. All text feature as one field + row normalization (Name- set3)
4. All text feature as seperate field + Column normalization of all feature (Name- set4)
5. All text feature as seperate field + Column normalization of originally numerical feature only (Name- set5)
6. All text feature as seperate field + row normalization (Name- set6)
7. All text feature as one field + No noramlization at all (Name- set7)
FOR EACH OF  ABOVE FIRST WE FEATURIZED DATA SET 2 TIMES  
* BOW for both categorical and text feature
* BOW for categorical feature and TF-IDF for text feature
## Decision Tree
1. Categorical - BOW , Text - TF-IDF ,Numerical - missing value imputation using median (Name- set8)
2. Categorical - BOW , Text - TF-IDF w2v ,Numerical - missing value imputation using median (Name- set9)
From first feature set i prepared another feature set which contains features who have non_zero feature importance.(Lets name it 'set 10'  for future reference)
## GBDT
1. categorical -Response coding , Text - TF-IDF , Numerical - standard normalization (Name- set11)
2. categorical -Response coding , Text - TF-IDF , Numerical - standard normalization
3. (Name- set12)
Both task is in same notebook file
## Logistic regression
1. Feature set set 11


## Model Performance

|SR. No.| Feature set | Model | Best hyperparameter | Auc Score |
| ------ | ------ | ------ | ------ | ------ |
|1|set 1 with BOW| Naive Bayes|0.0001|0.6767320754908597|
|2|set 1 with TF-IDF|Naive Bayes|0.001|0.6867195050820073|	
|3|set 2 with BOW|Naive Bayes|0.01|0.6799552487265281|
|4|set 2 with TF-IDF|Naive Bayes|0.01|0.6953310566942157|
|5|set 3 with BOW|Naive Bayes|0.001|0.654511748525141|
|6|set 3 with TF-IDF|Naive Bayes|0.0001|0.58705737463986|	
|7|set 4 with BOW|Naive Bayes|0.1|0.6790446713222033|
|8|set 4 with TF-IDF|Naive Bayes|0.1|0.6842498509955538|
|9|set 5 with BOW|Naive Bayes|1|0.691990321800742|
|10|set 5 with TF-IDF|Naive Bayes|0.1|0.6791352123015159|
|11|set 6 with BOW|Naive Bayes|0.0001|0.6713556341165524|
|12|set 6 with TF-IDF|Naive Bayes|0.001|0.6233539391879825|
|13|set 7 with BOW|Naive Bayes|0.001|0.6705230828509751|
|14|set 7 with TF-IDF|Naive Bayes|0.01|0.6129748010751123|
|15|set 8|Decision Tree|Min_split : 10, max_depth : 5|0.63242590840162|
|16|set 9|Decision Tree|Min_split : 10, max_depth : 5|0.6206837392724464|
|17|set 10|Logistic Regression|0.1|0.6506047470359109|
|18|set 11|GBDT|n_estimator:50 ,	Max Depth :2|0.69243089|
|19|set 12|GBDT|n_estimator	:100,MaxDepth : 3|0.7082633929|

- **NaiveBayes: Multinomial NB ,GBDT : XGBoost
##### Best Accuracy acchieved till now is 0.70

##### Future works:
* KNN
* MLP

* **   
* **
* **
#  THERE IS WILL, THERE IS WAY
## Thank you for visiting...                                          

