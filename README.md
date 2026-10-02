# Student Academic Performance Prediction Using Machine Learning

## Overview

This project uses supervised machine learning to predict whether a student is likely to achieve satisfactory academic performance based on demographic, academic, behavioural and social factors.

The project follows an end-to-end machine learning workflow covering data understanding, exploratory data analysis, data preparation, model building, evaluation and overfitting analysis.

## Objective

The objectives of this project are to:

- Analyse student-related data and identify relevant patterns.
- Prepare the dataset for machine learning.
- Build multiple classification models.
- Compare model performance using standard evaluation metrics.
- Analyse overfitting and model generalisation.
- Identify the model with the strongest test performance.

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

The earlier-period grades `G1` and `G2` are excluded from the model inputs because they are strongly related to the final grade and would make the prediction less useful.

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

These metrics were used to compare the four classification models and determine their performance on unseen test data.

## Results

The models were evaluated using **Accuracy, Precision, Recall, and F1 Score**.

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Logistic Regression | 63.29% | 70.69% | 77.36% | 73.87% |
| Decision Tree | 67.09% | 72.13% | 83.02% | 77.19% |
| Random Forest | 68.35% | 70.59% | 90.57% | 79.34% |
| KNN | 60.76% | 66.18% | 84.91% | 74.38% |

Random Forest achieved the highest **test accuracy (68.35%)** and **F1 Score (79.34%)** among the evaluated models. However, its 100% training accuracy indicated significant overfitting, which was further analysed and addressed through model tuning.

## Conclusion

This project demonstrated an end-to-end supervised machine learning workflow for predicting student academic performance. The process included data exploration, data preparation, feature selection, categorical encoding, model training, evaluation, and overfitting analysis.

Four classification models were compared, with **Random Forest** achieving the highest test accuracy of **68.35%** and F1 Score of **79.34%**. The results demonstrate how machine learning can identify patterns in historical student data and support data-driven analysis of academic performance.

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

## How to Run

1. Install the required dependencies:
```
pip install -r requirements.txt
```

2. Open Jupyter Notebook:
```
python -m notebook
```

3. Open `student_performance_prediction.ipynb`.

4. Run the notebook cells sequentially.
