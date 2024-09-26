# User Churn Prediction Task
## Problem Statement
You are provided with a dataset containing information about users playing video games. The goal is to predict whether a user will churn (i.e., stop playing the game).

## Approach
### Data Exploration
**Avg session time by churn**
![Alt text]("src/img/Avg session time by churn.png")

**churn by Gender**
![Alt text]("src/img/churn by Gender.png")

**Game genre vs Games played**
![Alt text]("src/img/Game genre vs Games played.png")

**total play time vs chur **
![Alt text]("src/img/total play time vs chur .png")


### Preprocessing
1. Converting categorical values into numerical values:-
    1. The column 'subscription_status' with values 'yes'or 'no' is converted into 1 and 0 respectively   
    2. One Hot encoding is done on the following columns game_genre','device_type','gender','favorite_game_mode' and first values of each column is removed so that it doesn't fall in dummy variable trap 
2. Feature Engineering:- Two new feature 'Play intensity' and 'interaction_per_session' are created on basis of existing data

3. Remove redundant columns:- Redundant columns are droped 

4. Column transformation:- I read on paper where it suggested that dataset should only consist of continuous columns or discrete columns and converting dataset to either of them gives better result. So I converted all the continuous columns into discrete columns using the formula suggested in the paper 
                    $$\[
N = \frac{x_{\text{min}} + x_{\text{max}}}{2}
\]

\[
\text{discrete\_value} = 
\begin{cases} 
\lfloor \frac{(x - x_{\text{min}}) \cdot N}{x_{\text{max}} - x_{\text{min}}} \rfloor & \text{if } x_{\text{max}} \neq x_{\text{min}} \\ 
0 & \text{otherwise} 
\end{cases}
\]$$
Discrete Value = ⌊ (Value - min) * ((max + min) / 2) / (max - min) ⌋

### Model Training 
Decision Tree with pruing is used for training beacause it is one of the best algorithm for non-linear classifications and it was faster than model with similar acuracy 
Accuracy - 68.79%

## Finding
1. The Dataset is provided is not a very quality dataset because none of columns are any way correlated to target variable this is one of the reason why i used Decision Tree, and this is reason why no algorithm could cross the benchmark of 68.79% 
2. The dataset is also imbalance with approx 69-31% i tried over sampling and under sampling but it doesn't help with the accuracy
![Alt text]("src/img/correlation.png")
3. Accuracy Of different Model :-
    1. Decision Tree with pruing- 68.79%
    2. Decision Tree without pruing- 57.65%
    3. Random Forest Classifier- 68.33%
    4. AdaBoost Classifier- 68.13%
    5. Bagging Classifier- 64%
    6. XGBoost Classifier- 64.26%
    7. Logistic Regression- 68.59%
    8. Naive Bayes(Gaussian)- 67.46%
    9. Deep Learning(architecture- 128-256-64-32)- 68.79%
    10. Deep Learning(architecture- 64-128-32)- 68.59%
    11. Percepton- 56.85%
    12. H2OAutoML- 51%
    13. TPOT Classifier- 63.26%
