# Obesity Level Prediction

This repository contains a supervised machine learning project designed to predict the **obesity level** of individuals based on lifestyle, dietary habits, and physical activity data. The project involves comprehensive **data preprocessing**, **exploratory data analysis (EDA)**, and the training of classification models using **Random Forest** and **XGBoost**.

---

## 📁 Dataset

**Source**: `1B.tsv`
**Format**: Tab-separated file
**Total Samples**: 2,111

### Attributes

* **Gender**: Gender of the individual
* **Birth Date**: Date of birth
* **Height**: Height (in meters)
* **Weight**: Weight (in kilograms)
* **Family History with Overweight**: Presence of overweight individuals in family
* **High Calorie Meal Frequency**: Frequency of consuming high-calorie meals
* **Veggies in Meals Frequency**: Frequency of vegetable intake
* **Daily Main Meals**: Number of main meals consumed daily
* **Snack Frequency**: Frequency of snack consumption
* **Smoking**: Whether the individual smokes (Yes/No)
* **Daily Water Consumption**: Daily water intake (in liters)
* **Weekly Physical Activity**: Average weekly physical activity
* **Alcohol Consumption**: Alcohol intake frequency
* **Transportation**: Main mode of transportation
* **Obesity Level**: Target label (7 classes of obesity)

---

## 🔍 Exploratory Data Analysis (EDA)

Key preprocessing steps:

* **Parsed date and numerical columns** (e.g., converted weight to float)
* **Created BMI feature** as:

  $$
  \text{BMI} = \frac{\text{Weight}}{\text{Height}^2}
  $$
* **Dropped irrelevant or highly correlated features** to reduce noise
* **Renamed** relevant columns for clarity
* **Handled duplicates and missing values**
* **Detected and validated absence of outliers** using IQR and visualizations (histogram, boxplot)

**Final Features for Modeling**:

* `Family Obesity History`
* `High Calorie Meal Freq`
* `Daily Water Consumption`
* `Weekly Physical Activity`
* `BMI`

---

## 🧪 Model Training

Two models were trained:

* **Random Forest Classifier**
* **XGBoost Classifier**

### Data Preparation

* **Label Encoding**: For binary categorical variables
* **Ordinal Encoding**: For target label (`Obesity Level`) based on severity
* **Feature Scaling**: StandardScaler applied to numerical inputs
* **Train-Test Split**: 80/20 split

### Target Classes

```
['Normal_Weight', 'Insufficient_Weight', 'Overweight_Level_I',
 'Overweight_Level_II', 'Obesity_Type_I', 'Obesity_Type_II', 'Obesity_Type_III']
```

### Evaluation Metrics

* Accuracy
* Precision, Recall, F1-Score
* Confusion Matrix

Example (Random Forest):

```text
              precision    recall  f1-score   support

         0.0       0.95      0.98      0.97        59
         1.0       0.98      0.96      0.97        57
         2.0       0.98      0.98      0.98        43
         3.0       0.96      0.98      0.97        48
         ...
```

---

## 🔧 Hyperparameter Tuning

Performed hyperparameter tuning using `RandomizedSearchCV` on the following:

### Random Forest:

* `n_estimators`: \[100, 200, 300]
* `max_depth`: \[5, 10, 20]
* `min_samples_split`: \[2, 5, 10]

### XGBoost:

* `learning_rate`: \[0.01, 0.1, 0.2]
* `max_depth`: \[3, 5, 7]
* `n_estimators`: \[100, 150, 200]

---

## 📚 Dependencies

```python
pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
```

Install all required libraries via pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

---

## 📈 Results

Both models achieved high classification performance, with F1-scores > 0.95 across all obesity categories. Further improvements can be made using ensemble methods and deeper feature engineering.

---

## 📌 Future Work

* Incorporate more lifestyle features (e.g., sleep, screen time)
* Expand dataset size for generalizability
* Experiment with deep learning classifiers
* Deploy as a web application for real-time prediction

---

## 📎 License

This project is for educational purposes only. Please cite the source dataset if reused for other studies.
