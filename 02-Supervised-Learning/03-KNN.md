# K-Nearest Neighbors (KNN)
---

# 1. What is KNN?

**K-Nearest Neighbors (KNN)** is a **supervised machine learning algorithm** used for:

* **Classification**
* **Regression**

KNN predicts the output of a new data point by looking at the **K closest data points** in the training data.

### Simple idea

> **“Similar data points usually have similar outcomes.”**

For example, if a new flower is very close to several flowers that are classified as *Setosa*, KNN can predict that the new flower is also *Setosa*.

---

# 2. Why is it called K-Nearest Neighbors?

The name itself explains the algorithm.

### K

The number of neighbors we consider.

Example:

```text
K = 3
```

means we look at the **3 nearest data points**.

### Nearest

The points having the smallest distance from the new point.

### Neighbors

Those nearby training data points.

Therefore:

> **KNN finds K nearest neighbors and uses them to make a prediction.**

---

# 3. Is KNN Supervised or Unsupervised?

KNN is a **supervised learning algorithm**.

Why?

Because the training data contains:

```text
Features (X) + Known Target (y)
```

Example:

| Height | Weight | Class |
| -----: | -----: | ----- |
|    150 |     45 | A     |
|    155 |     48 | A     |
|    180 |     80 | B     |
|    185 |     85 | B     |

The model uses the known classes to predict the class of a new observation.

### Interview answer

> **KNN is supervised because it learns from labeled training examples.**

---

# 4. How Does KNN Work?

KNN follows a simple process:

```text
New data point
      ↓
Choose K
      ↓
Calculate distance
from training points
      ↓
Find K nearest points
      ↓
Look at their target values
      ↓
Make prediction
```

For **classification**:

> Majority vote

For **regression**:

> Average or weighted average

---

# 5. Example of KNN Classification

Suppose we want to classify a new point.

We choose:

```text
K = 5
```

The five nearest neighbors are:

```text
Neighbor 1 → Red
Neighbor 2 → Blue
Neighbor 3 → Red
Neighbor 4 → Red
Neighbor 5 → Blue
```

Count:

```text
Red  → 3
Blue → 2
```

Majority = **Red**

Therefore:

```text
Prediction → Red
```

### Memory

> **KNN Classification → Majority vote**

---

# 6. Example of KNN Regression

Suppose we want to predict the price of a house.

We choose:

```text
K = 3
```

The three nearest houses have prices:

```text
₹50 lakh
₹55 lakh
₹60 lakh
```

KNN regression can calculate:

$$
\frac{50+55+60}{3}=55
$$

Therefore:

```text
Predicted price = ₹55 lakh
```

### Memory

> **KNN Regression → Average of neighbors**

With distance weighting, closer neighbors can have greater influence.

---

# 7. What is K?

`K` represents the **number of nearest neighbors** used for prediction.

Examples:

```text
K = 1 → 1 nearest neighbor
K = 3 → 3 nearest neighbors
K = 5 → 5 nearest neighbors
```

K is an important **hyperparameter**.

---

# 8. What Happens When K is Too Small?

Consider:

```text
K = 1
```

Only one neighbor determines the prediction.

Suppose the closest point happens to be a noisy or unusual observation.

Then the prediction can be affected heavily by that single point.

This can result in:

> **High variance and overfitting**

### Example

Suppose the neighbors around a new point are:

```text
A A A A B
```

If `K = 1` and the closest point is B:

```text
Prediction = B
```

Even though most nearby points are A.

---

# 9. What Happens When K is Too Large?

Suppose K is very large.

KNN considers many points, including points that may be relatively far away.

The model becomes less sensitive to local patterns.

This can result in:

> **High bias and underfitting**

### Example

Suppose a small region contains mostly Class A, but we choose a very large K and include many Class B points from farther away.

The local pattern may be lost.

---

# 10. Small K vs Large K

| Small K                          | Large K                 |
| -------------------------------- | ----------------------- |
| More sensitive to local patterns | Smoother predictions    |
| Lower bias                       | Higher bias             |
| Higher variance                  | Lower variance          |
| More sensitive to noise          | Less sensitive to noise |
| Can overfit                      | Can underfit            |

### Easy memory

```text
Small K → Flexible → High variance → Overfitting risk

Large K → Smooth → High bias → Underfitting risk
```

---

# 11. Bias in KNN

**Bias** is the error caused by a model being too simple or making overly strong assumptions.

In KNN:

```text
Very large K
      ↓
Very smooth decision
      ↓
May ignore local patterns
      ↓
Higher bias
      ↓
Possible underfitting
```

### Interview answer

> **Bias is error caused by overly simple assumptions in a model. In KNN, a very large K can increase bias.**

---

# 12. Variance in KNN

**Variance** describes how sensitive a model is to changes in the training data.

In KNN:

```text
Very small K
      ↓
Strongly influenced by nearby training points
      ↓
Sensitive to noise
      ↓
Higher variance
      ↓
Possible overfitting
```

### Interview answer

> **Variance is the sensitivity of a model to changes in its training data. In KNN, a very small K can lead to high variance.**

---

# 13. Bias-Variance Tradeoff

We want a balance between:

```text
Bias
  ↕
Variance
```

A model with:

* Too much bias → underfitting
* Too much variance → overfitting

For KNN:

```text
K increases
    ↓
Bias increases
    ↓
Variance decreases
```

Generally:

```text
Small K → Low Bias + High Variance

Large K → High Bias + Low Variance
```

The goal is to select a K that generalizes well to unseen data.

---

# 14. How Do We Choose K?

There is no universal best value of K.

We can try several values:

```text
K = 1
K = 3
K = 5
K = 7
K = 9
...
```

and evaluate their performance using validation data or **cross-validation**.

### Example

Suppose validation results are:

|  K | Accuracy |
| -: | -------: |
|  1 |      89% |
|  3 |      93% |
|  5 |      95% |
|  7 |      94% |
|  9 |      91% |

We would investigate the value that gives the best validation performance rather than choosing K randomly.

### Important

For binary classification, odd K values can reduce the chance of a voting tie, but **odd K is not automatically the best K**.

---

# 15. Distance in KNN

KNN needs to determine which points are closest.

Therefore, it uses **distance metrics**.

Common choices include:

* Euclidean distance
* Manhattan distance
* Minkowski distance

You already covered these in:

`02-Distance-Metrics.md`

### Basic process

```text
New point
    ↓
Calculate distance to training points
    ↓
Sort by distance
    ↓
Select K smallest distances
    ↓
Make prediction
```

---

# 16. Why Feature Scaling is Important in KNN

This is one of the **most important KNN interview questions**.

Suppose our features are:

```text
Age      → 18–60
Salary   → 20,000–2,00,000
```

Salary has much larger numerical values.

When calculating distance, salary can dominate the calculation.

Therefore, KNN is generally sensitive to feature scales.

### Example

Suppose:

```text
Point A → Age = 20, Salary = 50,000
Point B → Age = 21, Salary = 80,000
```

The difference in salary is much larger numerically than the difference in age.

Without appropriate scaling, the salary feature can have much greater influence on distance.

---

# 17. Standardization

A common scaling method is **Standardization**.

Formula:

$$
z=\frac{x-\mu}{\sigma}
$$

Where:

* `x` = original value
* `μ` = mean
* `σ` = standard deviation

In Python:

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

### Important

Use:

```python
fit_transform()
```

on training data.

Use:

```python
transform()
```

on test data.

Why?

Because the scaler should learn its statistics from the training data only.

This helps prevent **data leakage**.

---

# 18. What is a Lazy Learner?

KNN is called a **lazy learner**.

Why?

Because KNN does not build a traditional mathematical model during training.

It mainly stores the training examples and performs the major computation when a prediction is requested.

### Traditional algorithm

```text
Training
   ↓
Learn model
   ↓
Prediction
```

### KNN

```text
Training
   ↓
Store training data
   ↓
New point arrives
   ↓
Calculate distances
   ↓
Find neighbors
   ↓
Predict
```

### Interview answer

> **KNN is called a lazy learner because most of its computation is postponed until prediction time.**

---

# 19. KNN Training vs Prediction

### Training

Usually relatively inexpensive because KNN mainly stores the training data.

### Prediction

Can be expensive because the algorithm may need to calculate distances between the new point and many training points.

Therefore:

> **KNN generally has low training cost but potentially high prediction cost.**

This becomes especially important with large datasets.

---

# 20. Important KNN Hyperparameters

A common Scikit-learn KNN classifier is:

```python
KNeighborsClassifier(
    n_neighbors=5,
    weights="uniform",
    metric="minkowski",
    p=2
)
```

Let's understand each parameter.

---

## `n_neighbors`

Controls K.

```python
n_neighbors=5
```

means:

> Consider the 5 nearest neighbors.

---

## `weights`

Controls how much influence each neighbor has.

### `weights="uniform"`

Every neighbor has equal importance.

Example:

```text
Neighbor 1 → 1 vote
Neighbor 2 → 1 vote
Neighbor 3 → 1 vote
```

### `weights="distance"`

Closer neighbors have more influence.

```text
Very close → More influence
Farther     → Less influence
```

### Interview answer

> **Uniform weighting gives equal importance to neighbors, while distance weighting gives greater influence to closer neighbors.**

---

# 21. `metric`

Specifies the distance metric.

Examples:

```python
metric="euclidean"
```

or:

```python
metric="manhattan"
```

or:

```python
metric="minkowski"
```

---

# 22. What is `p`?

When using Minkowski distance:

```text
p = 1 → Manhattan
p = 2 → Euclidean
```

For example:

```python
KNeighborsClassifier(
    n_neighbors=5,
    metric="minkowski",
    p=2
)
```

uses Euclidean distance through the Minkowski formulation.

---

# 23. KNN Classification vs Regression

|                    | Classification         | Regression               |
| ------------------ | ---------------------- | ------------------------ |
| Target             | Categorical            | Numerical                |
| Prediction         | Majority vote          | Average/weighted average |
| Scikit-learn class | `KNeighborsClassifier` | `KNeighborsRegressor`    |
| Example            | Spam / Not Spam        | House price              |

---

# 24. Example: KNN for Classification

Imagine a medical dataset where we want to classify a sample as:

```text
Disease
No Disease
```

For a new patient, KNN finds the nearest patients.

Suppose:

```text
K = 5
```

Nearest neighbors:

```text
Patient 1 → Disease
Patient 2 → No Disease
Patient 3 → Disease
Patient 4 → Disease
Patient 5 → No Disease
```

Count:

```text
Disease    → 3
No Disease → 2
```

Prediction:

```text
Disease
```

This is the basic idea of KNN classification.

---

# 25. Example: KNN for Regression

Suppose we want to predict house price.

The nearest houses have:

```text
₹40 lakh
₹45 lakh
₹50 lakh
₹55 lakh
₹60 lakh
```

For:

```text
K = 5
```

Prediction:

$$
\frac{40+45+50+55+60}{5}=50
$$

Therefore:

```text
Predicted price = ₹50 lakh
```

---

# 26. Curse of Dimensionality

This is an important KNN interview topic.

As the number of features increases, data points become increasingly sparse in the feature space.

Consequently, the distinction between "near" and "far" can become less useful.

This is called the:

> **Curse of dimensionality**

### Why is it a problem for KNN?

KNN depends on meaningful distances.

If we have too many dimensions:

```text
More features
     ↓
Data becomes sparse
     ↓
Distances become less informative
     ↓
Finding meaningful neighbors becomes harder
```

### Possible solutions

* Remove irrelevant features
* Feature selection
* Dimensionality reduction
* PCA where appropriate

---

# 27. Advantages of KNN

### 1. Simple to understand

The basic idea is intuitive.

### 2. Easy to implement

Libraries such as Scikit-learn provide simple implementations.

### 3. Supports classification and regression

### 4. Can model nonlinear relationships

KNN does not require a straight-line relationship between features and target.

### 5. Few assumptions about the underlying data distribution

It is a flexible, instance-based approach.

---

# 28. Disadvantages of KNN

### 1. Prediction can be slow

It may need to compare a new point against many training points.

### 2. Sensitive to feature scaling

Different feature ranges can distort distances.

### 3. Sensitive to irrelevant features

Unimportant features can affect distance calculations.

### 4. Sensitive to noise

Especially when K is very small.

### 5. Curse of dimensionality

Performance can suffer with many features.

### 6. Memory usage

The training data needs to be retained for prediction.

---

# 29. When Should You Use KNN?

KNN can be useful when:

* The dataset is small or moderate in size.
* Similar observations tend to have similar outcomes.
* A meaningful distance measure exists.
* Features can be properly scaled.
* You want a simple baseline model.
* Prediction speed is not extremely critical.

---

# 30. When Should You Be Careful With KNN?

Be careful when:

* Dataset is extremely large.
* There are many irrelevant features.
* Dimensionality is very high.
* Distance is not meaningful.
* Features have very different scales.
* Very fast predictions are required.
* Memory is limited.

---

# 31. KNN vs K-Means

This is a **very common interview question**.

| Feature                   | KNN                         | K-Means            |
| ------------------------- | --------------------------- | ------------------ |
| Learning type             | Supervised                  | Unsupervised       |
| Uses labels?              | Yes                         | No                 |
| Main task                 | Classification / Regression | Clustering         |
| Meaning of K              | Number of neighbors         | Number of clusters |
| Uses distance?            | Yes                         | Yes                |
| Training labels required? | Yes                         | No                 |

### Interview answer

> **KNN is a supervised algorithm that uses the K nearest labeled points to make a prediction, whereas K-Means is an unsupervised algorithm that divides unlabeled data into K clusters.**

---

# 32. KNN vs Linear Regression

| Feature         | KNN                       | Linear Regression                      |
| --------------- | ------------------------- | -------------------------------------- |
| Learning        | Supervised                | Supervised                             |
| Main tasks      | Classification/Regression | Regression                             |
| Basic idea      | Nearby examples           | Learn linear relationship              |
| Distance-based  | Yes                       | No                                     |
| Scaling         | Important                 | Usually not required for basic fitting |
| Model type      | Instance-based            | Parametric                             |
| Prediction cost | Can be high               | Usually low                            |

---

# 33. KNN vs Decision Tree

| Feature        | KNN               | Decision Tree          |
| -------------- | ----------------- | ---------------------- |
| Distance-based | Yes               | No                     |
| Scaling        | Usually important | Generally not required |
| Training       | Minimal/lazy      | Builds tree            |
| Prediction     | Can be expensive  | Usually fast           |
| Classification | Yes               | Yes                    |
| Regression     | Yes               | Yes                    |

---

# 34. Important Interview Questions

### Q1. What is KNN?

> KNN is a supervised learning algorithm that predicts a new observation using its K nearest training examples.

### Q2. What does K represent?

> K represents the number of nearest neighbors considered during prediction.

### Q3. Is KNN supervised or unsupervised?

> Supervised.

### Q4. Can KNN be used for regression?

> Yes. KNN regression generally predicts using the average or distance-weighted average of neighboring target values.

### Q5. How does KNN classify a new point?

> It finds the K nearest training points and assigns the class with the majority vote.

### Q6. What happens when K is too small?

> The model becomes sensitive to noise, increasing variance and the risk of overfitting.

### Q7. What happens when K is too large?

> The model becomes too smooth, increasing bias and the risk of underfitting.

### Q8. Why is feature scaling important in KNN?

> Because KNN uses distance, and features with larger numerical ranges can dominate the distance calculation.

### Q9. Why is KNN called a lazy learner?

> Because it mainly stores training data and performs most computation during prediction.

### Q10. What distance metrics can KNN use?

> Euclidean, Manhattan, Minkowski, and other supported distance metrics depending on the data and problem.

### Q11. What is `n_neighbors`?

> It specifies the number of neighbors used by KNN.

### Q12. What is the difference between uniform and distance weighting?

> Uniform gives equal importance to neighbors; distance weighting gives more influence to closer neighbors.

### Q13. What is the curse of dimensionality?

> As the number of features increases, data becomes sparse and distance-based neighborhood relationships can become less meaningful.

### Q14. How do you select K?

> Evaluate different K values using validation or cross-validation and select a value that generalizes well.

### Q15. What is the difference between KNN and K-Means?

> KNN is supervised and uses labeled neighbors for prediction, while K-Means is unsupervised and groups unlabeled data into clusters.

### Q16. Does KNN have a training phase?

> It has a minimal training phase compared with many traditional algorithms, mainly involving storing the training data; most computation happens during prediction.

### Q17. What is the biggest computational disadvantage of KNN?

> Prediction can become expensive because distances may need to be calculated against many stored training examples.

### Q18. What happens if irrelevant features are included?

> They can distort distance calculations and reduce prediction quality.

### Q19. Why can KNN struggle with high-dimensional data?

> Because of the curse of dimensionality, where distance becomes less informative as dimensionality increases.

### Q20. What is the difference between KNN classification and regression?

> Classification uses neighbor voting, while regression uses numerical aggregation such as an average or weighted average.

---

# 35. 📝 One-Line Interview Revision

```text
KNN
→ Supervised learning algorithm

Tasks
→ Classification + Regression

K
→ Number of nearest neighbors

Classification
→ Majority vote

Regression
→ Average / weighted average

Distance
→ Finds nearest neighbors

Common distances
→ Euclidean, Manhattan, Minkowski

Scaling
→ Important because KNN is distance-based

Small K
→ Low bias, high variance, overfitting risk

Large K
→ High bias, low variance, underfitting risk

Lazy learner
→ Most computation happens during prediction

Training
→ Mainly stores training examples

Prediction
→ Calculate distances → Find K neighbors → Predict

Weights
→ Uniform or distance-based

High dimensions
→ Curse of dimensionality

Major limitation
→ Prediction can be expensive
```

---

# 36. 🧠 KNN Memory Map

```text
                         KNN
                          │
              ┌───────────┴───────────┐
              │                       │
        Supervised                K = Neighbors
              │
        ┌─────┴─────┐
        │           │
 Classification  Regression
        │           │
 Majority Vote   Average
        │           │
        └─────┬─────┘
              │
       Calculate Distance
              │
      ┌───────┼────────┐
      │       │        │
  Euclidean Manhattan Minkowski
              │
        Feature Scaling
              │
         StandardScaler
              │
        Choose / Tune K
              │
      ┌───────┴────────┐
      │                │
 Small K            Large K
      │                │
 High Variance      High Bias
      │                │
Overfitting Risk   Underfitting Risk
```

---

# 37. 📝 Interview Explanation — 30 Seconds

If an interviewer says:

**“Explain KNN.”**

You can answer:

> **KNN, or K-Nearest Neighbors, is a supervised machine learning algorithm used for classification and regression. For a new data point, it calculates its distance from the training points, selects the K nearest neighbors, and uses majority voting for classification or averaging for regression. Since KNN is distance-based, feature scaling is important when features have different ranges. KNN is called a lazy learner because it mainly stores the training data and performs most of the computation during prediction. A very small K can cause high variance and overfitting, while a very large K can cause high bias and underfitting.**

---

# 38. ⭐ What You Should Actually Remember

Don't try to memorize the entire chapter word-for-word.

Understand this flow:

```text
KNN
 ↓
Supervised
 ↓
New point
 ↓
Calculate distance
 ↓
Find K nearest points
 ↓
Classification → Majority
Regression → Average
 ↓
Scaling is important
 ↓
Choose K carefully
 ↓
Small K → Overfitting risk
Large K → Underfitting risk
 ↓
Lazy learner
 ↓
Prediction can be expensive
 ↓
Curse of dimensionality
```

