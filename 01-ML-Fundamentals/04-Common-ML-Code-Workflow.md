
## Common ML Code — Learn This Pattern

```python
# ============================================================
# COMMON MACHINE LEARNING CODE WORKFLOW
# ============================================================

# 1. Import Libraries
import pandas as pd

# 2. Load Dataset
data = pd.read_csv("dataset.csv")

# 3. Understand Dataset
print(data.head())
print(data.info())
print(data.describe())

# Check missing values
print(data.isnull().sum())

# Check duplicate rows
print(data.duplicated().sum())

# ============================================================
# 4. DATA PREPROCESSING
# ============================================================

# 4.1 Remove duplicate rows
data = data.drop_duplicates()

# 4.2 Handle missing values
# Numerical column → use median/mean
# data["Age"] = data["Age"].fillna(data["Age"].median())

# Categorical column → use mode
# data["City"] = data["City"].fillna(data["City"].mode()[0])

# 4.3 Encode categorical columns
# Use when categorical input features are present
# data = pd.get_dummies(data, columns=["City"], drop_first=True)

# ============================================================
# 5. SEPARATE FEATURES AND TARGET
# ============================================================

X = data.iloc[:, :-1]
y = data.iloc[:, -1]

# ============================================================
# 6. TRAIN-TEST SPLIT
# ============================================================

from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

# ============================================================
# 7. FEATURE SCALING — ONLY IF REQUIRED
# ============================================================

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)


# ============================================================
# 8. CREATE MODEL
# ============================================================

# Change this according to the algorithm

# Example:
# from sklearn.neighbors import KNeighborsClassifier
# model = KNeighborsClassifier(n_neighbors=5)


# ============================================================
# 9. TRAIN MODEL
# ============================================================

# model.fit(X_train, y_train)


# ============================================================
# 10. MAKE PREDICTIONS
# ============================================================

# y_pred = model.predict(X_test)


# ============================================================
# 11. EVALUATE MODEL
# ============================================================

# Classification example:
# from sklearn.metrics import accuracy_score
# print("Accuracy:", accuracy_score(y_test, y_pred))


# Regression example:
# from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
# print("MAE:", mean_absolute_error(y_test, y_pred))
# print("MSE:", mean_squared_error(y_test, y_pred))
# print("R2:", r2_score(y_test, y_pred))


# ============================================================
# 12. NEW PREDICTION
# ============================================================

# new_data = [[value1, value2, value3]]

# If scaling was used:
# new_data = scaler.transform(new_data)

# prediction = model.predict(new_data)

# print("Prediction:", prediction)
```

# What Each Step Does

### 1. Import pandas

```python
import pandas as pd
```

**What it does:** Imports Pandas.

**Why:** Used to load and work with datasets.

---

### 2. Load Dataset

```python
data = pd.read_csv("dataset.csv")
```

**What it does:** Reads the CSV file and stores it in `data`.

**Why:** We need the dataset before performing ML.

---

### 3. Understand Dataset

```python
print(data.head())
print(data.info())
print(data.describe())
```

* `head()` → shows first few rows
* `info()` → shows columns, data types, missing values
* `describe()` → gives statistical summary of numerical columns

**Why:** Before building a model, we need to understand the data.

---

### 4. Separate X and y

```python
X = data.iloc[:, :-1]
y = data.iloc[:, -1]
```

* `X` → **features/input**
* `y` → **target/output**

Example:

| Age | Salary | Experience | Purchased |
| --: | -----: | ---------: | --------- |
|  22 |  25000 |          1 | No        |
|  30 |  50000 |          5 | Yes       |

Here:

```text
X = Age, Salary, Experience
y = Purchased
```

---

### 5. Preprocessing

This step depends on the dataset and algorithm.

Possible preprocessing:

```text
Missing values
      ↓
Duplicates
      ↓
Encoding
      ↓
Scaling
      ↓
Feature selection/engineering
```

**Why:** Real-world data may not be directly suitable for ML.

---

### 6. Train-Test Split

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.2,
    random_state=42
)
```

**What it does:** Divides the dataset into:

```text
Dataset
   ↓
 ┌───────────────┐
 │ Training 80%  │ → Model learns
 └───────────────┘
 ┌───────────────┐
 │ Testing 20%   │ → Model is evaluated
 └───────────────┘
```

* `X_train`, `y_train` → training data
* `X_test`, `y_test` → testing data
* `test_size=0.2` → 20% testing
* `random_state=42` → same split each time

---

### 7. Create Model

```python
model = AlgorithmName()
```

**What it does:** Creates the ML algorithm/model.

Example:

```python
model = KNeighborsClassifier(n_neighbors=2)
```

or

```python
model = LinearRegression()
```

or

```python
model = DecisionTreeClassifier()
```

**This is one of the main parts that changes between algorithms.**

---

### 8. Train Model

```python
model.fit(X_train, y_train)
```

**What it does:** Gives the training data to the model so it can learn patterns.

```text
X_train + y_train
       ↓
   model.fit()
       ↓
    Learning
```

---

### 9. Make Predictions

```python
y_pred = model.predict(X_test)
```

**What it does:** Uses the trained model to predict outputs for unseen test data.

```text
X_test
   ↓
Trained Model
   ↓
Predicted output
   ↓
y_pred
```

---

### 10. Evaluate Model

```python
metric(y_test, y_pred)
```

**What it does:** Compares:

```text
Actual output     vs     Predicted output
   y_test                  y_pred
```

For classification:

```text
Accuracy
Precision
Recall
F1-score
```

For regression:

```text
MAE
MSE
RMSE
R²
```

---

### 11. New Prediction

```python
new_data = [[value1, value2, value3]]
model.predict(new_data)
```

**What it does:** Uses the trained model to predict the result for completely new data.

Example:

```python
model.predict([[25, 40000, 3]])
```

---

# 🧠 The Pattern You Should Memorize

```text
1. Load
      ↓
2. Understand
      ↓
3. X and y
      ↓
4. Preprocess
      ↓
5. Train-Test Split
      ↓
6. Create Model
      ↓
7. Fit / Train
      ↓
8. Predict
      ↓
9. Evaluate
      ↓
10. New Prediction
```


**Common steps:**
Load → Understand → X/y → Split → Fit → Predict → Evaluate

**Steps that can change:**
Preprocessing → Algorithm → Hyperparameters → Evaluation metric

