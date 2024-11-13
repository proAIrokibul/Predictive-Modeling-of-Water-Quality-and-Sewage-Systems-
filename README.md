# Sewage System Classification Project

## Project Overview

In this project, the goal is to predict the condition of a sewage system based on environmental data such as geographical location, nitrogen and phosphorus levels, and sampling date. The dataset consists of 8,016 samples, each with features including **Geographical Location (Latitude)**, **Geographical Location (Longitude)**, **Sampling Date**, **Nitrogen (mg/L)**, **Phosphorus (mg/L)**, and **State of Sewage System** as the target variable. The target variable is categorical with three possible values representing different states of the sewage system.

To solve this classification problem, three different machine learning classifiers were evaluated:
1. **Logistic Regression**
2. **Random Forest Classifier**
3. **XGBoost Classifier**

Each model was evaluated on accuracy, precision, recall, F1-score, and confusion matrix to assess its performance.

## Data Preprocessing

Before building the models, the dataset underwent preprocessing steps:
- **Missing values handling**: Any missing or null values were addressed using imputation techniques.
- **Feature encoding**: Categorical variables such as "State of Sewage System" were encoded to numerical values.
- **Normalization/Standardization**: The continuous features like **Nitrogen (mg/L)** and **Phosphorus (mg/L)** were normalized to a standard scale.
- **Date Parsing**: The **Sampling Date** was parsed to extract useful information such as year and month for temporal analysis.

## Model Evaluation and Results

### 1. Logistic Regression Classifier

#### Accuracy: 
**50.29%**

#### Classification Report:

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.50      | 1.00   | 0.67     | 4031    |
| 1     | 0.00      | 0.00   | 0.00     | 2519    |
| 2     | 0.00      | 0.00   | 0.00     | 1466    |

**Accuracy**: 50.29%

- The Logistic Regression model performed poorly, with the **precision** and **recall** for classes `1` and `2` being 0.
- The **confusion matrix** shows that the model is unable to predict classes `1` and `2`, as all predictions are concentrated in class `0`.


### 2. Random Forest Classifier

#### Accuracy: 
**99.60%**

#### Classification Report:

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.99      | 1.00   | 1.00     | 4031    |
| 1     | 1.00      | 0.99   | 1.00     | 2519    |
| 2     | 1.00      | 0.99   | 1.00     | 1466    |

**Accuracy**: 99.60%

- The Random Forest model performed exceptionally well, with nearly perfect precision, recall, and F1-scores across all classes.
- **Confusion Matrix**:
  - Most predictions were correctly classified, but there were a few misclassifications between classes `1` and `0` and class `2`.


### 3. XGBoost Classifier

#### Accuracy: 
**82.40%**

#### Classification Report:

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.77      | 0.97   | 0.86     | 4031    |
| 1     | 0.91      | 0.73   | 0.81     | 2519    |
| 2     | 0.96      | 0.58   | 0.72     | 1466    |

**Accuracy**: 82.40%

- The XGBoost model performed reasonably well, with strong precision for class `2` and good recall for class `0`.
- There is some misclassification, especially between classes `1` and `2`.


## Analysis and Comparison

### Logistic Regression:
- **Strengths**: Simple and fast to implement, easy to interpret.
- **Weaknesses**: It struggled significantly with class imbalance and failed to classify classes `1` and `2`, leading to very poor performance. Logistic Regression is not suitable for this dataset due to its linear nature and inability to capture complex patterns.

### Random Forest Classifier:
- **Strengths**: Outstanding performance with near-perfect accuracy, high precision, recall, and F1-scores across all classes. Random Forests handle class imbalances better and are less likely to underfit.
- **Weaknesses**: Potential overfitting due to the model's high accuracy. It may not generalize well to new, unseen data if the model is too complex.
- **Recommendation**: This model is highly effective for this problem, but regularization techniques and cross-validation should be used to prevent overfitting.

### XGBoost Classifier:
- **Strengths**: Balanced performance across all classes, with solid precision and recall. It handled class imbalance better than Logistic Regression and is less prone to overfitting than Random Forest.
- **Weaknesses**: Slight misclassifications between certain classes, and recall for class `2` was lower than expected.
- **Recommendation**: XGBoost provides a good trade-off between performance and interpretability. It should be fine-tuned further to optimize recall for all classes.

## Conclusion

- **Best Model**: The **Random Forest Classifier** delivered the best results with nearly perfect accuracy and class-specific performance.
- **XGBoost** provided a balanced and robust model with strong precision and recall for each class.
- **Logistic Regression** performed poorly due to its inability to handle complex, non-linear relationships in the data.




