# `01-Supervised-Learning.md`

Paste the following **directly into GitHub**:

# Supervised Learning

## 1. Definition

**Supervised Learning** is a type of Machine Learning where a model learns from **labeled data**.

The dataset contains:

* **Input features (X)**
* **Known target/output (y)**

The model learns the relationship between `X` and `y` and uses it to predict the output for new data.

---

## 2. How Supervised Learning Works

```text
Labeled Dataset
      ↓
Features (X) + Target (y)
      ↓
Train-Test Split
      ↓
Model Training
      ↓
Model learns relationship
      ↓
Test Data
      ↓
Prediction
      ↓
Evaluation
```

### Example

Suppose we have student data:

| Hours Studied | Attendance | Result |
| ------------: | ---------: | ------ |
|             2 |         60 | Fail   |
|             5 |         80 | Pass   |
|             7 |         90 | Pass   |

Here:

```text
Features (X) → Hours Studied, Attendance
Target (y)   → Result
```

The model learns from the known results and predicts the result for a new student.

---

# 3. Main Types of Supervised Learning

Supervised Learning is mainly divided into:

```text
Supervised Learning
       │
       ├── Classification
       │
       └── Regression
```

---

# 4. Classification

**Classification** is a supervised learning problem where the target is a **category or class**.

### Examples

```text
Spam / Not Spam
Pass / Fail
Disease / No Disease
Cat / Dog
```

### Example

If the target is:

```text
Pass
Fail
```

the model predicts one of these classes.

### Common Classification Algorithms

* Logistic Regression
* K-Nearest Neighbors (KNN)
* Naive Bayes
* Decision Tree
* Random Forest
* Support Vector Machine (SVM)

---

# 5. Regression

**Regression** is a supervised learning problem where the target is a **continuous numerical value**.

### Examples

```text
House Price
Salary
Temperature
Sales
Student Marks
```

### Example

If the target is:

```text
₹45,000
₹62,000
₹78,000
```

the model predicts a numerical value.

### Common Regression Algorithms

* Linear Regression
* Multiple Linear Regression
* Polynomial Regression
* Ridge Regression
* Lasso Regression
* Decision Tree Regression
* Random Forest Regression

---

# 6. Classification vs Regression

| Classification                  | Regression                 |
| ------------------------------- | -------------------------- |
| Predicts a class/category       | Predicts a numerical value |
| Output is discrete              | Output is continuous       |
| Example: Spam/Not Spam          | Example: House Price       |
| Accuracy, Precision, Recall, F1 | MAE, MSE, RMSE, R²         |

---

# 7. Labeled Data

**Labeled data** means the dataset contains the correct target/output for each observation.

Example:

| Age | Salary | Purchased |
| --: | -----: | --------- |
|  22 |  25000 | No        |
|  30 |  50000 | Yes       |
|  35 |  70000 | Yes       |

Here, `Purchased` is the label/target.

---

# 8. Unlabeled Data

In **unlabeled data**, there is no known target/output column.

Example:

| Age | Salary |
| --: | -----: |
|  22 |  25000 |
|  30 |  50000 |
|  35 |  70000 |

There is no target column.

This type of data is generally used in **Unsupervised Learning**.

---

# 9. Training in Supervised Learning

During training, the model receives:

```text
Features (X) + Known Target (y)
```

The model learns patterns and relationships between the input and output.

---

# 10. Prediction

After training, the model receives new input data and predicts the target.

```text
New Data
   ↓
Trained Model
   ↓
Prediction
```

Example:

```text
Hours Studied = 6
Attendance = 85%
        ↓
     Model
        ↓
      Pass
```

---

# 11. Model Evaluation

After making predictions, we compare the predicted values with the actual values.

### Classification Metrics

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC

### Regression Metrics

* MAE
* MSE
* RMSE
* R²

---

# 12. Advantages

* Learns from labeled examples.
* Can be used for both classification and regression.
* Performance can be evaluated using known target values.
* Useful for prediction and decision-making tasks.

---

# 13. Disadvantages

* Requires labeled data.
* Collecting and labeling data can be time-consuming.
* Poor-quality labels can affect model performance.
* The model may overfit the training data.

---

# 14. Common Applications

### Classification

* Spam detection
* Fraud detection
* Disease classification
* Customer churn prediction
* Sentiment classification

### Regression

* House price prediction
* Sales prediction
* Demand forecasting
* Salary prediction
* Temperature prediction

---

# 15. Common Supervised Learning Algorithms

| Algorithm           | Type                        |
| ------------------- | --------------------------- |
| Linear Regression   | Regression                  |
| Logistic Regression | Classification              |
| KNN                 | Classification / Regression |
| Naive Bayes         | Classification              |
| Decision Tree       | Classification / Regression |
| Random Forest       | Classification / Regression |
| SVM                 | Classification / Regression |

---

# 16. Supervised Learning Workflow

```text
1. Collect Dataset
       ↓
2. Understand Dataset
       ↓
3. Clean & Preprocess
       ↓
4. Separate X and y
       ↓
5. Train-Test Split
       ↓
6. Select Algorithm
       ↓
7. Train Model
       ↓
8. Make Predictions
       ↓
9. Evaluate Model
       ↓
10. Improve Model
       ↓
11. Predict New Data
```

---

# 📝 Interview Quick Revision

**What is Supervised Learning?**
Supervised Learning is a type of Machine Learning where a model learns from labeled data containing input features and known target outputs.

**What are the two main types?**
Classification and Regression.

**What is Classification?**
Classification predicts a categorical or class-based output.

**What is Regression?**
Regression predicts a continuous numerical output.

**What is labeled data?**
Data containing both input features and the known target/output.

**Give an example of classification.**
Spam or Not Spam prediction.

**Give an example of regression.**
House price prediction.

**Why is it called supervised?**
Because the model learns using known target outputs, which guide the learning process.

---

# ⭐ Key Takeaway

```text
Supervised Learning
        ↓
Learns from Labeled Data
        ↓
      X + y
        ↓
 ┌──────┴──────┐
 ↓             ↓
Classification Regression
 ↓             ↓
Classes       Numbers
```

