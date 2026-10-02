# Student Academic Performance Prediction Using Machine Learning

## Overview

This project uses supervised machine learning to predict whether a student is likely to achieve satisfactory academic performance based on demographic, academic, behavioural and social factors.

The project follows an end-to-end machine learning workflow covering data understanding, exploratory data analysis, data preparation, model building, evaluation, overfitting analysis and prediction of new student performance.

## Objective

The objectives of this project are to:

- Analyse student-related data and identify relevant patterns.
- Prepare the dataset for machine learning.
- Build multiple classification models.
- Compare model performance using standard evaluation metrics.
- Analyse overfitting and model generalisation.
- Use the trained model to predict the performance of a new student.

## Dataset

The project uses the **Student Performance** dataset from the UCI Machine Learning Repository.

The dataset contains student information related to school, demographics, family background, study habits, social factors and academic performance.

For this project, the Mathematics dataset (`student-mat.csv`) is used.

Source: UCI Machine Learning Repository  
Dataset: Student Performance  
DOI: 10.24432/C5TG7T

The dataset is licensed under **CC BY 4.0**. Appropriate attribution is provided to the original source.

## Machine Learning Problem

- **Learning Type:** Supervised Learning
- **Problem Type:** Binary Classification
- **Target:** Student Performance

The final grade (`G3`) is converted into:

- `G3 >= 10` → Pass
- `G3 < 10` → Fail

Previous grades (`G1` and `G2`) are included as input features because they provide information about the student's earlier academic performance. The final grade (`G3`) is excluded from the model inputs because it is used to create the Pass/Fail target.

## Workflow

```text
Business Understanding
        ↓
Dataset Understanding
        ↓
Exploratory Data Analysis
        ↓
Data Preparation
        ↓
Model Building
        ↓
Model Evaluation
        ↓
Overfitting Analysis
        ↓
Final Recommendation
        ↓
Student Performance Prediction
        ↓
Prediction Analysis
```

## Models Used

The following machine learning classification models were implemented and compared:

1. **Logistic Regression**
   - A linear classification model used as a baseline.
   - Works well when the relationship between features and the target is approximately linear.

2. **Decision Tree**
   - Uses a tree-like structure to make predictions based on feature conditions.
   - Easy to interpret and does not require feature scaling.

3. **Random Forest**
   - An ensemble of multiple decision trees.
   - Combines predictions from several trees to improve generalisation and prediction performance.

4. **K-Nearest Neighbors (KNN)**
   - Classifies a student based on the classes of nearby data points.
   - Feature scaling was applied before training.

## Evaluation Metrics

The models were evaluated using the following metrics:

- **Accuracy:** Measures the overall percentage of correctly classified students.
- **Precision:** Measures how many of the students predicted as **Pass** actually passed.
- **Recall:** Measures how many of the actual **Pass** students were correctly identified.
- **F1 Score:** Combines Precision and Recall into a single metric, providing a balanced measure of model performance.

These metrics were used to compare the four classification models on unseen test data.

## Results

The models were evaluated using **Accuracy, Precision, Recall, and F1 Score**.

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 84.81% | 93.62% | 83.02% | 88.00% |
| Decision Tree | 86.08% | 97.73% | 81.13% | 88.66% |
| Random Forest | 87.34% | 95.74% | 84.91% | 90.00% |
| KNN | 69.62% | 72.31% | 88.68% | 79.66% |

Random Forest achieved the highest **test accuracy (87.34%)** and **F1 Score (90.00%)** among the evaluated models.

### Random Forest Confusion Matrix

| Actual / Predicted | Fail | Pass |
|---|---:|---:|
| **Fail** | 24 | 2 |
| **Pass** | 8 | 45 |

## Overfitting Analysis

Training and testing accuracy were compared to identify possible overfitting.

| Model | Training Accuracy | Testing Accuracy |
|---|---:|---:|
| Logistic Regression | 97.15% | 84.81% |
| Decision Tree | 98.73% | 86.08% |
| Random Forest | 100.00% | 87.34% |
| KNN | 81.96% | 69.62% |

The original Random Forest achieved 100% training accuracy and 87.34% testing accuracy, indicating some overfitting.

A tuned Random Forest was also tested:

- **Training Accuracy:** 96.20%
- **Testing Accuracy:** 86.08%

The tuning reduced the training accuracy and therefore reduced overfitting, but it also slightly reduced test accuracy. Therefore, the original Random Forest was retained as the final model because it provided the strongest test performance among the evaluated models.

## Student Performance Prediction

The trained Random Forest model can be used to predict whether a new student is likely to **Pass** or **Fail** based on previous grades and other student-related factors.

The prediction also displays the model's estimated probabilities for the Pass and Fail classes.

For example:

```text
Predicted Performance: Pass
Probability of Fail: 7.00%
Probability of Pass: 93.00%
```

These probabilities represent the model's estimated support for each class and should not be interpreted as a guarantee of the student's actual outcome.

## Prediction Analysis

Feature importance was analysed to understand which features the Random Forest relied on most across its predictions.

The top 10 features were:

| Feature | Importance |
|---|---:|
| G2 | 35.78% |
| G1 | 19.81% |
| failures | 4.35% |
| absences | 3.82% |
| goout | 2.78% |
| age | 2.51% |
| Walc | 1.96% |
| health | 1.79% |
| Medu | 1.64% |
| Fedu | 1.63% |

Previous grades (`G1` and `G2`) had the highest feature importance in the trained Random Forest, followed by previous failures and absences.

Feature importance represents the model's reliance on these features during prediction. It should not be interpreted as a direct cause-and-effect relationship.

## Conclusion

This project demonstrated an end-to-end supervised machine learning workflow for predicting student academic performance. The process included data exploration, data preparation, feature selection, categorical encoding, model training, evaluation, overfitting analysis and prediction of new student performance.

Four classification models were compared, with **Random Forest** achieving the highest test accuracy of **87.34%** and F1 Score of **90.00%**. The trained model was also used to make predictions for new student inputs and analyse feature importance.

## Technologies Used

- Python
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## Project Structure

```text
student-performance-ml/
├── student_performance_prediction.ipynb
├── student-mat.csv
├── README.md
└── requirements.txt
```

- **student_performance_prediction.ipynb** – Complete machine learning implementation and analysis.
- **student-mat.csv** – Student performance dataset used for training and evaluation.
- **README.md** – Project documentation.
- **requirements.txt** – Required Python libraries.

## How to Run

1. Install the required dependencies:

```bash
pip install -r requirements.txt
```

2. Open Jupyter Notebook:

```bash
python -m notebook
```

3. Open `student_performance_prediction.ipynb`.

4. Run the notebook cells sequentially.
