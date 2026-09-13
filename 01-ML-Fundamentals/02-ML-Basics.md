# Machine Learning Basics

This file covers the fundamental concepts and terminology required before learning Machine Learning algorithms.

---

## 1. Dataset

A **dataset** is a collection of data used for analysis and Machine Learning.

- **Rows** → Observations / records
- **Columns** → Features / variables

> **Remember:** Dataset = Collection of observations and variables.

---

## 2. Feature

A **feature** is an input variable used by a Machine Learning model to make predictions.

Example:

Age, Salary, Experience

> **Remember:** Feature = Input variable.

---

## 3. Target

The **target** is the output variable that the model tries to predict.

Example:

Features → Age, Salary, Experience  
Target → Purchased

> **Remember:** Target = Output to predict.

---

## 4. X and y

In Machine Learning:

- **X** → Features / Input
- **y** → Target / Output

> **Remember:** X = Input, y = Output.

---

## 5. Observation

An **observation** is one individual record or instance in a dataset.

> **Remember:** Observation = One row/record.

---

## 6. Training Data

**Training data** is the portion of the dataset used to teach the Machine Learning model.

> **Remember:** Training data → Learn.

---

## 7. Testing Data

**Testing data** is used to evaluate the model on unseen data.

- Training Data → Learn
- Testing Data → Evaluate

> **Remember:** Testing data → Evaluate.

---

## 8. Validation Data

**Validation data** is used to tune the model and select the best model or hyperparameters.

- Training → Learn
- Validation → Tune / Select
- Testing → Final Evaluation

---

## 9. Model

A **Machine Learning model** is the learned representation of patterns from training data.

> **Remember:** Model = Learned patterns used for prediction.

---

## 10. Algorithm

An **algorithm** is a method used to learn patterns from data.

Examples:

- Linear Regression
- Logistic Regression
- KNN
- Decision Tree
- Random Forest
- SVM
- K-Means

> **Algorithm = Method used for learning.**

> **Model = Learned result.**

---

## 11. Training

**Training** is the process of learning patterns from training data.

> **Remember:** Training = Learning from data.

---

## 12. Prediction

A **prediction** is the output produced by a trained model for new data.

> **Remember:** Prediction = Model output.

---

## 13. Inference

**Inference** is the process of using a trained model to make predictions on new, unseen data.

> **Remember:** Inference = Using a trained model on new data.

---

## 14. Parameters

**Parameters** are values learned automatically by the model from training data.

Example in Linear Regression:

**y = mx + c**

Here, `m` and `c` are learned parameters.

> **Remember:** Parameters are learned from data.

---

## 15. Hyperparameters

**Hyperparameters** are settings chosen by the user to control the learning process.

Examples:

- K in KNN
- Maximum depth in Decision Tree
- Number of trees in Random Forest
- Learning rate in Gradient Boosting

### Parameter vs Hyperparameter

| Parameter | Hyperparameter |
|---|---|
| Learned from data | Set by user |
| Learned during training | Chosen by user |
| Example: model coefficient | Example: K in KNN |

> **Remember:** Parameters are learned; hyperparameters are configured.

---

## 16. fit() and predict()

### fit()

Used to train the model.

**fit() → Learn**

### predict()

Used to generate predictions.

**predict() → Predict**

> **Remember:** fit() → Learn, predict() → Predict.

---

## 17. Classification

**Classification** is a supervised learning task where the model predicts a category or class.

Examples:

- Email → Spam / Not Spam
- Student → Pass / Fail
- Transaction → Fraud / Not Fraud

> **Classification → Predict a category.**

---

## 18. Regression

**Regression** is a supervised learning task where the model predicts a continuous numerical value.

Examples:

- House → Price
- Employee → Salary
- Company → Sales

> **Regression → Predict a numerical value.**

---

## 19. Generalization

**Generalization** is the ability of a Machine Learning model to perform well on new, unseen data.

> **Remember:** Generalization = Good performance on unseen data.

---

## 20. Overfitting

**Overfitting** occurs when a model learns the training data too closely, including noise and unnecessary details.

- Training Performance → Very Good
- Testing Performance → Poor

### Causes

- Model too complex
- Too little training data
- Too many irrelevant features
- Excessive training

> **Remember:** Overfitting = Good training performance but poor unseen-data performance.

---

## 21. Underfitting

**Underfitting** occurs when a model is too simple to learn important patterns.

- Training Performance → Poor
- Testing Performance → Poor

### Causes

- Model too simple
- Insufficient training
- Missing important features
- Excessive regularization

> **Remember:** Underfitting = Model fails to learn important patterns.

---

## 22. Overfitting vs Underfitting

| Overfitting | Underfitting |
|---|---|
| Model too complex | Model too simple |
| Learns noise | Misses important patterns |
| Training performance high | Training performance low |
| Testing performance poor | Testing performance poor |
| High variance | High bias |

### Ideal Model

Good Training Performance + Good Testing Performance = Good Generalization

---

## 23. Bias

**Bias** is the error caused by overly simple assumptions in a model.

> **High Bias → Usually Underfitting**

---

## 24. Variance

**Variance** is the error caused by a model being highly sensitive to the training data.

> **High Variance → Usually Overfitting**

---

## 25. Bias-Variance Tradeoff

The **bias-variance tradeoff** is the balance between model simplicity and model complexity to achieve good generalization.

> **Interview Point:** The goal is to find a balance between bias and variance for good generalization.

---

## 26. Model Complexity

**Model complexity** refers to how flexible or complicated a model is.

- Low Complexity → May Underfit
- High Complexity → May Overfit

> **Remember:** Too simple → Underfitting, too complex → Overfitting.

---

## 27. Training Error and Testing Error

### Training Error

Error measured on the training data.

### Testing Error

Error measured on unseen testing data.

A good model should perform well on both training and unseen data.

---

## 28. Data Leakage

**Data leakage** occurs when information that should not be available during training is accidentally used by the model.

This can produce unrealistically high performance.

> **Remember:** Data Leakage = Unwanted information enters the training process.

---

# 29. Machine Learning Workflow

1. Problem Definition
2. Load Dataset
3. Understand Data
4. Clean Data
5. EDA
6. Select Features and Target
7. Preprocess Data
8. Train/Test Split
9. Choose Algorithm
10. Train Model
11. Make Predictions
12. Evaluate Model
13. Improve Model

### Short Version

**Problem → Data → Preprocessing → Training → Prediction → Evaluation → Improvement**

---

# 30. Important ML Terms — Quick Revision

| Term | Meaning |
|---|---|
| Dataset | Collection of data |
| Feature | Input variable |
| Target | Output to predict |
| Observation | One record |
| X | Input features |
| y | Target |
| Training Data | Data used to learn |
| Validation Data | Data used for tuning |
| Testing Data | Data used for evaluation |
| Algorithm | Method used for learning |
| Model | Learned patterns |
| Training | Learning from data |
| Prediction | Model output |
| Inference | Prediction on new data |
| Parameter | Value learned from data |
| Hyperparameter | User-defined setting |
| Generalization | Performance on unseen data |
| Overfitting | Learns training data too closely |
| Underfitting | Fails to learn important patterns |
| Bias | Error from simple assumptions |
| Variance | Sensitivity to training data |
| Data Leakage | Unwanted information enters training |

---

# 31. Interview Quick Revision

### What is a feature?

A feature is an input variable used by a Machine Learning model to make predictions.

### What is a target?

The target is the output variable that the model tries to predict.

### Parameter vs Hyperparameter?

Parameters are learned from training data, whereas hyperparameters are settings chosen to control the learning process.

### What is overfitting?

Overfitting occurs when a model learns the training data too closely and performs poorly on unseen data.

### What is underfitting?

Underfitting occurs when a model is too simple to learn important patterns from the data.

### What is generalization?

Generalization is the ability of a model to perform well on unseen data.

### What is data leakage?

Data leakage occurs when information that should not be available during training is used by the model.

### Training vs Testing Data?

Training data is used to learn the model, while testing data is used to evaluate the model on unseen data.

### Algorithm vs Model?

An algorithm is the method used to learn patterns, while a model is the learned result.

---

# 32. Final Revision

## 10 Things to Remember

1. X = Features
2. y = Target
3. Training Data = Learn
4. Testing Data = Evaluate
5. Validation Data = Tune
6. Algorithm = Learning method
7. Model = Learned patterns
8. Parameter = Learned value
9. Hyperparameter = Configured value
10. Good Model = Good Generalization

---

## Next Topic

**Data Preprocessing**

Topics:

- Missing Values
- Duplicates
- Categorical Data
- Encoding
- Outliers
- Feature Scaling
- Feature Selection
- Feature Engineering
- Data Leakage
