Absolutely. This time I’ll give you the **entire file content without the outer ` ```markdown ` and ` ``` `**, so you can paste it directly into GitHub's **Edit** box.

**File name:** `03-Data-Preprocessing.md`

Copy from `# Data Preprocessing` to the very last line.

# Data Preprocessing

Data preprocessing is the process of **cleaning, transforming, and preparing raw data** before using it to train a Machine Learning model.

Real-world datasets are rarely perfect. They may contain missing values, duplicate records, incorrect data types, categorical variables, outliers, and different feature scales.

> **Goal:** Convert raw data into a clean and suitable form for Machine Learning.

---

## 1. Why is Data Preprocessing Important?

Machine Learning models learn patterns from data.

If the input data is poor, the model may learn incorrect or misleading patterns.

Common problems in real-world datasets:

* Missing values
* Duplicate records
* Incorrect data types
* Categorical variables
* Outliers
* Different feature scales
* Irrelevant features
* Noisy data
* Inconsistent values
* Data leakage

### Basic Process

Raw Data
↓
Understand Data
↓
Clean Data
↓
Transform Data
↓
Feature Selection / Engineering
↓
Train Model
↓
Evaluate Model

> **Important:** Not every dataset requires every preprocessing step. The required steps depend on the dataset, problem, and algorithm.

---

## 2. Understanding the Dataset

Before preprocessing, first understand what the dataset contains.

Important things to inspect:

* Number of rows
* Number of columns
* Column names
* Data types
* Missing values
* Duplicate records
* Unique values
* Numerical features
* Categorical features
* Target variable
* Target distribution
* Possible outliers

### Questions to Ask

1. What does one row represent?
2. What does each column represent?
3. Which column is the target?
4. Which columns are features?
5. Which features are numerical?
6. Which features are categorical?
7. Are there missing values?
8. Are there duplicate records?
9. Are there unusual values?
10. Does the algorithm require feature scaling?

> **Best Practice:** Understand the dataset before deciding how to preprocess it.

---

## 3. Types of Data

Data used in Machine Learning can be broadly divided into:

* Numerical Data
* Categorical Data
* Boolean Data
* Text Data
* Date/Time Data

---

## 3.1 Numerical Data

Numerical data contains numbers representing measurable or countable quantities.

Examples:

* Age
* Salary
* Height
* Weight
* Experience
* Temperature

Numerical data can be divided into two types.

### Discrete Data

Values that are countable.

Examples:

* Number of students
* Number of rooms
* Number of purchases

### Continuous Data

Values that can take a range of numerical values.

Examples:

* Height
* Weight
* Temperature
* Salary

---

## 3.2 Categorical Data

Categorical data represents groups or categories.

Examples:

* Gender
* City
* Department
* Education Level
* Product Type
* Payment Method

Example:

| City      |
| --------- |
| Hyderabad |
| Chennai   |
| Mumbai    |
| Hyderabad |

Most Machine Learning algorithms require numerical input, so categorical variables often need to be converted into numerical representations.

This process is called **Encoding**.

---

## 3.3 Boolean Data

Boolean data contains two possible values.

Examples:

* True / False
* Yes / No
* 0 / 1

Depending on the algorithm and data representation, boolean values may be converted into numerical values.

---

## 3.4 Text Data

Text data contains natural language.

Examples:

* Customer Review
* Email
* Product Description
* News Article

Text usually requires specialized preprocessing techniques such as:

* Tokenization
* Stop-word handling
* Stemming
* Lemmatization
* Vectorization

Text preprocessing is mainly used in **Natural Language Processing (NLP)** problems.

---

## 3.5 Date and Time Data

Date/time columns can contain information such as:

* Date
* Time
* Year
* Month
* Day
* Hour

Useful features can sometimes be extracted from date/time data.

For example:

```text
Date of Birth → Age
Date → Year, Month, Day, Day of Week
```

This is an example of **Feature Engineering**.

---

# 4. Missing Values

A **missing value** occurs when information is unavailable for a particular observation.

Example:

| Age | Salary | Experience |
| --: | -----: | ---------: |
|  22 |  25000 |          1 |
|  25 |      — |          2 |
|  30 |  50000 |          — |

Here, Salary and Experience contain missing values.

---

## 4.1 Why Are Missing Values a Problem?

Missing values can:

* Prevent some algorithms from training
* Reduce the amount of usable data
* Affect statistical calculations
* Introduce bias
* Affect model performance

However, missing values should not automatically be deleted.

First understand **why the data is missing**.

---

# 5. Methods to Handle Missing Values

Common methods include:

1. Remove rows
2. Remove columns
3. Mean imputation
4. Median imputation
5. Mode imputation
6. Advanced imputation

---

## 5.1 Remove Rows

Rows containing missing values can be removed when:

* Only a small number of rows are affected
* The missing information is not important
* Removing the rows does not introduce significant bias

> Removing too many rows can result in loss of valuable information.

---

## 5.2 Remove Columns

A column may be removed when:

* It contains a very large proportion of missing values
* It provides little useful information
* The feature is not important for the problem

---

## 5.3 Mean Imputation

Missing numerical values are replaced with the mean of the feature.

Mean imputation can work reasonably well when the feature is approximately symmetric and does not contain severe outliers.

> **Interview Point:** Mean is sensitive to extreme values.

---

## 5.4 Median Imputation

Missing numerical values are replaced with the median.

Median is often preferred when:

* Data is skewed
* Outliers are present

The median is less sensitive to extreme values than the mean.

> **Interview Point:** Median is generally more robust to outliers than mean.

---

## 5.5 Mode Imputation

Missing categorical values can be replaced with the most frequently occurring category.

This is called **Mode Imputation**.

Example:

```text
Red
Blue
Blue
Blue
Missing
```

The missing value can be replaced with:

```text
Blue
```

because Blue is the mode.

---

## 5.6 Advanced Imputation

More advanced methods include:

* KNN Imputation
* Iterative Imputation
* Model-based imputation

These methods can use relationships between features to estimate missing values.

> **Best Practice:** Choose the imputation method based on the dataset and the reason values are missing.

---

# 6. Duplicates

A **duplicate** is a repeated record in a dataset.

Example:

| Name | Age | Salary |
| ---- | --: | -----: |
| A    |  22 |  30000 |
| B    |  25 |  40000 |
| A    |  22 |  30000 |

The first and third rows may be duplicate records.

---

## Why Can Duplicates Be a Problem?

Duplicates can:

* Give certain observations more importance
* Distort statistics
* Affect model training
* Introduce bias

However, repeated records are not always errors.

For example, two identical purchases could represent two genuine transactions.

> **Best Practice:** Investigate duplicates before removing them.

---

# 7. Data Types

Correct data types are important for analysis and Machine Learning.

Common data types include:

### Integer

Whole numbers.

Examples:

* Age
* Number of Rooms
* Years of Experience

### Float

Decimal values.

Examples:

* Height
* Weight
* Temperature

### String

Text values.

Examples:

* Name
* City
* Department

### Boolean

Logical values.

Examples:

* True / False
* Yes / No

Incorrect data types can cause problems during preprocessing and model training.

---

# 8. Categorical Data Encoding

**Encoding** is the process of converting categorical variables into numerical representations that Machine Learning algorithms can process.

Common encoding techniques:

* Label Encoding
* One-Hot Encoding
* Ordinal Encoding

The correct technique depends on whether the categories have a meaningful order.

---

# 9. Label Encoding

**Label Encoding** assigns an integer to each category.

Example:

```text
Low    → 0
Medium → 1
High   → 2
```

This can be appropriate when the categories have a meaningful order:

```text
Low < Medium < High
```

### Important Warning

Suppose we have:

```text
Red
Blue
Green
```

If we encode them as:

```text
Red   → 0
Blue  → 1
Green → 2
```

the numbers may incorrectly suggest that:

```text
Red < Blue < Green
```

when no such relationship exists.

> **Interview Point:** Be careful when using integer encoding for nominal categories because some models may interpret the numbers as ordered.

---

# 10. One-Hot Encoding

**One-Hot Encoding** creates a separate binary column for each category.

Suppose:

```text
City

Hyderabad
Chennai
Mumbai
```

It can become:

| Hyderabad | Chennai | Mumbai |
| --------: | ------: | -----: |
|         1 |       0 |      0 |
|         0 |       1 |      0 |
|         0 |       0 |      1 |

Each row receives:

* `1` → Belongs to the category
* `0` → Does not belong to the category

### When is One-Hot Encoding Useful?

It is commonly used for **nominal categorical variables** where categories do not have a natural order.

> **Remember:** One-Hot Encoding → Separate binary columns.

---

# 11. Ordinal Encoding

**Ordinal Encoding** is used when categories have a meaningful order.

Example:

```text
Poor       → 0
Average    → 1
Good       → 2
Excellent  → 3
```

The order is preserved:

```text
Poor < Average < Good < Excellent
```

> **Remember:** Ordinal Encoding → Categories have a meaningful order.

---

# 12. Encoding Comparison

| Method           | Main Use                             |
| ---------------- | ------------------------------------ |
| Label Encoding   | Assigns integer labels to categories |
| One-Hot Encoding | Nominal categories                   |
| Ordinal Encoding | Ordered categories                   |

### Quick Rule

```text
No meaningful order
        ↓
One-Hot Encoding

Meaningful order
        ↓
Ordinal Encoding
```

---

# 13. Outliers

An **outlier** is an observation that is unusually far from the other observations.

Example:

```text
Salary:

25000
28000
30000
32000
31000
500000  ← Potential outlier
```

---

## 13.1 Why Do Outliers Matter?

Outliers can:

* Distort the mean
* Increase variance
* Influence regression models
* Affect distance calculations
* Affect some scaling methods
* Influence statistical analysis

However:

> **An outlier is not automatically an error.**

It may represent a genuine observation.

---

# 14. Detecting Outliers

Common methods include:

* IQR Method
* Z-Score
* Box Plot
* Domain-specific rules

---

## 14.1 IQR Method

IQR stands for **Interquartile Range**.

Formula:

```text
IQR = Q3 - Q1
```

Where:

* Q1 = First Quartile
* Q3 = Third Quartile

Common boundaries:

```text
Lower Bound = Q1 - 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR
```

Values outside these boundaries are commonly treated as potential outliers.

> **Note:** This is a rule for identifying potential outliers, not proof that a value is incorrect.

---

## 14.2 Z-Score

The Z-score measures how far a value is from the mean in terms of standard deviations.

Formula:

```text
Z = (x - μ) / σ
```

Where:

* `x` = observation
* `μ` = mean
* `σ` = standard deviation

A large absolute Z-score may indicate a potential outlier.

---

# 15. Handling Outliers

Possible approaches include:

### 1. Keep the Outlier

Use this when the value is genuine and meaningful.

### 2. Remove the Outlier

Use this when the value is clearly incorrect or irrelevant.

### 3. Cap the Value

Replace extreme values with selected upper or lower limits.

### 4. Transform the Feature

Transformations can reduce the influence of extreme values.

### 5. Use Robust Methods

Some algorithms and statistical techniques are less sensitive to outliers.

> **Best Practice:** Investigate the reason for an outlier before deciding what to do with it.

---

# 16. Feature Scaling

**Feature scaling** is the process of transforming numerical features so that their scales are comparable.

Example:

```text
Age        → 18 to 70
Salary     → 20,000 to 200,000
Experience → 0 to 30
```

Salary has a much larger numerical scale than Age.

For some algorithms, this can affect the result significantly.

---

# 17. Why Is Feature Scaling Important?

Scaling is especially important for algorithms that depend on:

* Distance
* Magnitude
* Similarity
* Gradient-based optimization

Examples:

* KNN
* K-Means
* SVM
* PCA
* Logistic Regression
* Neural Networks

Tree-based algorithms generally do not require feature scaling:

* Decision Tree
* Random Forest
* Gradient Boosting
* XGBoost

> **Important:** Scaling requirements depend mainly on the algorithm.

---

# 18. Standardization

**Standardization** transforms a feature so that it has approximately:

```text
Mean = 0
Standard Deviation = 1
```

Formula:

```text
z = (x - μ) / σ
```

Where:

* `x` = original value
* `μ` = mean
* `σ` = standard deviation

A common implementation is:

```text
StandardScaler
```

### Important

Standardization does **not** mean all values become between 0 and 1.

> **Remember:** Standardization → Mean approximately 0 and Standard Deviation approximately 1.

---

# 19. Normalization

**Normalization** commonly transforms values to a fixed range, often:

```text
0 to 1
```

A common Min-Max formula is:

```text
x' = (x - xmin) / (xmax - xmin)
```

A common implementation is:

```text
MinMaxScaler
```

> **Remember:** Normalization commonly scales values to a bounded range such as 0 to 1.

---

# 20. Standardization vs Normalization

| Standardization                    | Normalization                                 |
| ---------------------------------- | --------------------------------------------- |
| Mean approximately 0               | Commonly scales to a fixed range              |
| Standard deviation approximately 1 | Often 0 to 1                                  |
| Uses mean and standard deviation   | Uses minimum and maximum                      |
| Values are not restricted to 0–1   | Values are bounded when using Min-Max scaling |

### Memory Trick

```text
Standardization
→ Mean ≈ 0
→ Standard Deviation ≈ 1

Normalization
→ Fixed range
→ Commonly 0 to 1
```

---

# 21. Robust Scaling

**Robust Scaling** uses statistics that are less affected by outliers.

It commonly uses:

* Median
* Interquartile Range (IQR)

Robust scaling can be useful when numerical features contain significant outliers.

### Comparison

| Method          | Main Idea                   | Outlier Sensitivity |
| --------------- | --------------------------- | ------------------- |
| Standardization | Mean and standard deviation | More sensitive      |
| Min-Max Scaling | Minimum and maximum         | More sensitive      |
| Robust Scaling  | Median and IQR              | Less sensitive      |

> **Remember:** Robust Scaling → Median + IQR.

---

# 22. Feature Selection

**Feature Selection** is the process of selecting the most useful existing features for a Machine Learning model.

Suppose a dataset contains:

```text
Age
Salary
Experience
Customer ID
Phone Number
```

Customer ID and Phone Number may not provide useful predictive information.

Useful features might be:

```text
Age
Salary
Experience
```

### Benefits of Feature Selection

* Reduces unnecessary features
* Can reduce overfitting
* Can improve model performance
* Reduces computational cost
* Improves interpretability

> **Remember:** Feature Selection = Select useful existing features.

---

# 23. Feature Engineering

**Feature Engineering** is the process of creating, transforming, or combining features to make them more useful for Machine Learning.

Example:

```text
Date of Birth
      ↓
     Age
```

Another example:

```text
Total Purchase Amount
Number of Purchases
        ↓
Average Purchase Amount
```

Feature engineering often uses domain knowledge.

> **Remember:** Feature Engineering = Create or transform useful features.

---

# 24. Feature Selection vs Feature Engineering

| Feature Selection            | Feature Engineering                    |
| ---------------------------- | -------------------------------------- |
| Selects existing features    | Creates or transforms features         |
| Removes unnecessary features | Creates useful representations         |
| Example: Remove Customer ID  | Example: Create Age from Date of Birth |

---

# 25. Data Leakage

**Data leakage** occurs when information that should not be available during model training accidentally influences the training process.

Data leakage can produce:

* Unrealistically high performance
* Incorrect evaluation
* Poor real-world performance

### Example

Suppose we want to predict whether a student will pass.

If the dataset contains:

```text
Final Exam Result
```

and we use the final result itself to predict whether the student passes, the model is receiving information that would only be known after the outcome.

This is leakage.

```text
Future Information
       ↓
Training Data
       ↓
Data Leakage
       ↓
Unrealistically Good Results
```

> **Remember:** Information unavailable at prediction time should not be used to make the prediction.

---

# 26. Data Leakage During Preprocessing

Data leakage can also happen during preprocessing.

### Incorrect Approach

```text
Entire Dataset
      ↓
Calculate preprocessing statistics
      ↓
Train/Test Split
```

The test set has influenced the preprocessing.

### Correct Approach

```text
Dataset
   ↓
Train/Test Split
   ↓
Training Data
   ↓
Learn preprocessing parameters
   ↓
Transform Training Data

Same learned parameters
   ↓
Transform Testing Data
```

For transformations that learn information from data:

```text
Training Data → fit + transform
Testing Data  → transform only
```

For example, a scaler should be fitted using training data only.

> **Interview Point:** Fit preprocessing transformations only on training data to prevent data leakage.

---

# 27. Train-Test Split and Preprocessing

A common safe workflow is:

```text
Raw Dataset
     ↓
Separate Features and Target
     ↓
Train/Test Split
     ↓
Fit Preprocessing on Training Data
     ↓
Transform Training Data
     ↓
Transform Testing Data
     ↓
Train Model
     ↓
Evaluate Model
```

The central principle is:

> **The test set must remain unseen when learning preprocessing parameters or making training decisions.**

---

# 28. Preprocessing and Different Algorithms

Different Machine Learning algorithms have different preprocessing requirements.

| Algorithm           | Scaling Usually Needed?     |
| ------------------- | --------------------------- |
| Linear Regression   | Often beneficial            |
| Logistic Regression | Often beneficial            |
| KNN                 | Yes                         |
| Naive Bayes         | Depends on variant and data |
| Decision Tree       | Usually No                  |
| Random Forest       | Usually No                  |
| SVM                 | Yes                         |
| K-Means             | Yes                         |
| PCA                 | Yes                         |
| Gradient Boosting   | Usually No                  |
| XGBoost             | Usually No                  |
| Neural Networks     | Usually beneficial          |

### Why?

Algorithms such as KNN, K-Means, SVM, and PCA are sensitive to feature scale or distance.

Tree-based algorithms generally use feature thresholds and are therefore usually insensitive to feature scaling.

---

# 29. Imbalanced Data

A classification dataset is **imbalanced** when one class contains many more observations than another class.

Example:

```text
Class 0 → 950 samples
Class 1 → 50 samples
```

The dataset is highly imbalanced.

---

## Why Is Class Imbalance a Problem?

A model may achieve high accuracy by mostly predicting the majority class while performing poorly on the minority class.

For example:

```text
Accuracy = 95%
```

may look good, but the model could simply predict the majority class for almost every observation.

---

## Common Approaches

Possible techniques include:

* Oversampling
* Undersampling
* SMOTE
* Class weights
* Threshold adjustment
* Appropriate evaluation metrics

Common metrics for imbalanced classification:

* Precision
* Recall
* F1-score
* PR-AUC
* ROC-AUC

> **Interview Point:** Accuracy alone may be misleading for imbalanced datasets.

---

# 30. Feature Transformation

Sometimes a feature's distribution makes modeling difficult.

Feature transformations can help represent the data more effectively.

Common transformations include:

* Log transformation
* Square-root transformation
* Power transformations

For example, a heavily right-skewed feature may sometimes benefit from a logarithmic transformation.

> **Important:** Transformations should be selected based on the data distribution and model requirements.

---

# 31. Data Preprocessing Pipeline

A practical preprocessing pipeline can look like:

```text
                    Dataset
                       ↓
                Understand Data
                       ↓
               Identify Features
                       ↓
                Identify Target
                       ↓
                Train/Test Split
                       ↓
             ┌─────────┴─────────┐
             ↓                   ↓
        Numerical Data      Categorical Data
             ↓                   ↓
        Handle Missing       Handle Missing
             ↓                   ↓
           Scaling             Encoding
             └─────────┬─────────┘
                       ↓
                Feature Selection
                       ↓
                Feature Engineering
                       ↓
                  Train Model
                       ↓
                    Evaluate
```

> **Note:** Not every dataset requires every step.

---

# 32. Common Preprocessing Mistakes

## Mistake 1: Preprocessing Without Understanding the Data

Not every dataset requires the same preprocessing steps.

---

## Mistake 2: Removing All Outliers

Some outliers are genuine observations.

---

## Mistake 3: Using the Wrong Encoding

Using arbitrary integer labels for nominal categories can introduce artificial ordering.

---

## Mistake 4: Scaling Before Splitting

Calculating scaling statistics using the entire dataset can cause data leakage.

---

## Mistake 5: Using Test Data for Feature Selection

The test set should remain isolated until final evaluation.

---

## Mistake 6: Assuming Scaling Is Always Required

Tree-based algorithms generally do not require scaling.

---

## Mistake 7: Ignoring the Meaning of Missing Values

A missing value may contain useful information about the real-world process.

---

## Mistake 8: Using Accuracy for Every Classification Problem

Accuracy can be misleading when classes are highly imbalanced.

> **Best Practice:** Always connect preprocessing decisions to the dataset, business problem, and selected algorithm.

---

# 33. End-to-End Preprocessing Checklist

Before training a Machine Learning model:

* [ ] Understand the dataset
* [ ] Identify features
* [ ] Identify target
* [ ] Check data types
* [ ] Check missing values
* [ ] Check duplicates
* [ ] Identify numerical features
* [ ] Identify categorical features
* [ ] Encode categorical variables when required
* [ ] Investigate outliers
* [ ] Check class imbalance
* [ ] Select useful features
* [ ] Engineer useful features when needed
* [ ] Decide whether scaling is required
* [ ] Split data correctly
* [ ] Prevent data leakage
* [ ] Train the model
* [ ] Evaluate the model

---

# 34. 📝 Quick Revision

| Concept             | Key Point                                                    |
| ------------------- | ------------------------------------------------------------ |
| Data Preprocessing  | Preparing raw data for Machine Learning                      |
| Missing Values      | Handle unavailable information appropriately                 |
| Duplicates          | Identify repeated records                                    |
| Data Types          | Ensure columns have appropriate types                        |
| Encoding            | Convert categorical variables into numerical representations |
| Label Encoding      | Assigns integer labels                                       |
| One-Hot Encoding    | Creates binary columns for categories                        |
| Ordinal Encoding    | Represents ordered categories                                |
| Outliers            | Unusually distant observations                               |
| IQR                 | Common method for identifying potential outliers             |
| Z-Score             | Measures distance from the mean in standard deviations       |
| Feature Scaling     | Makes numerical feature scales comparable                    |
| Standardization     | Mean ≈ 0 and standard deviation ≈ 1                          |
| Normalization       | Commonly scales values to 0–1                                |
| Robust Scaling      | Uses median and IQR                                          |
| Feature Selection   | Selects useful existing features                             |
| Feature Engineering | Creates or transforms useful features                        |
| Data Leakage        | Prevents unavailable information from influencing training   |
| Class Imbalance     | Unequal distribution of target classes                       |

---

# 35. 🧠 Interview Questions

### 1. What is data preprocessing?

> Data preprocessing is the process of cleaning, transforming, and preparing raw data before using it to train a Machine Learning model.

### 2. Why is data preprocessing important?

> Real-world data may contain missing values, duplicates, categorical variables, outliers, inconsistent formats, and different feature scales. Preprocessing makes the data suitable for Machine Learning.

### 3. How do you handle missing values?

> Depending on the dataset, missing values can be handled by removing rows or columns, using mean, median, or mode imputation, or applying advanced imputation techniques.

### 4. When would you use median instead of mean?

> Median is often preferred when the data is skewed or contains outliers because it is less sensitive to extreme values.

### 5. What is encoding?

> Encoding converts categorical variables into numerical representations that Machine Learning algorithms can process.

### 6. What is the difference between Label Encoding and One-Hot Encoding?

> Label Encoding assigns integer values to categories, while One-Hot Encoding creates separate binary columns for categories.

### 7. When is One-Hot Encoding preferred?

> One-Hot Encoding is commonly preferred for nominal categorical variables where categories do not have a meaningful order.

### 8. What is Ordinal Encoding?

> Ordinal Encoding represents categorical variables with a meaningful order using numerical values.

### 9. What is an outlier?

> An outlier is an observation that is unusually far from the other observations.

### 10. Should we always remove outliers?

> No. An outlier may be a genuine observation. It should be investigated before deciding whether to keep, remove, cap, or transform it.

### 11. What is the IQR?

> IQR stands for Interquartile Range and is calculated as Q3 minus Q1. It is commonly used to identify potential outliers.

### 12. What is feature scaling?

> Feature scaling transforms numerical features so that their scales are comparable.

### 13. Why is scaling important for KNN?

> KNN uses distance calculations. If features have different scales, a large-scale feature can dominate the distance calculation.

### 14. Why doesn't a Decision Tree usually require scaling?

> Decision Trees make decisions using feature thresholds rather than distance calculations, so their performance is generally insensitive to feature scale.

### 15. What is Standardization?

> Standardization transforms a feature so that it has approximately mean 0 and standard deviation 1.

### 16. What is Normalization?

> Normalization commonly scales values to a fixed range such as 0 to 1.

### 17. Standardization vs Normalization?

> Standardization uses the mean and standard deviation, while normalization commonly uses minimum and maximum values to scale data to a fixed range.

### 18. What is Feature Selection?

> Feature Selection is the process of selecting the most useful existing features for a Machine Learning model.

### 19. What is Feature Engineering?

> Feature Engineering is the process of creating, transforming, or combining features to make them more useful for Machine Learning.

### 20. What is Data Leakage?

> Data leakage occurs when information that should not be available during training influences the model or preprocessing process.

### 21. How can preprocessing cause data leakage?

> Leakage can occur when preprocessing statistics are learned using the test set. Transformations that learn from data should generally be fitted on the training set and then applied to the test set.

### 22. What is class imbalance?

> Class imbalance occurs when the target classes have significantly different numbers of observations.

### 23. Why can accuracy be misleading for imbalanced data?

> A model can achieve high accuracy by mostly predicting the majority class while performing poorly on the minority class.

### 24. Which metrics can be useful for imbalanced classification?

> Precision, Recall, F1-score, PR-AUC, and ROC-AUC can be useful depending on the problem and the relative costs of different errors.

---

# 36. ⭐ Interview Memory Map

```text
                    DATA PREPROCESSING
                           │
          ┌────────────────┼────────────────┐
          ↓                ↓                ↓
        CLEAN           TRANSFORM          SELECT
          │                │                │
   Missing Values       Encoding       Feature Selection
   Duplicates           Scaling
   Data Types           Outliers
                        Feature
                        Engineering
          │                │
          └────────┬───────┘
                   ↓
             Check Imbalance
                   ↓
            Prevent Leakage
                   ↓
              Train Model
                   ↓
                Evaluate
```

---

# 37. Final Takeaways

1. Understand the dataset before preprocessing.
2. Handle missing values based on the data and problem.
3. Investigate duplicates before removing them.
4. Choose encoding based on the type of categorical variable.
5. Do not remove outliers without investigating them.
6. Scale features when the selected algorithm requires or benefits from it.
7. Feature Selection selects useful existing features.
8. Feature Engineering creates or transforms useful features.
9. Keep the test set isolated from training decisions.
10. Prevent data leakage at every stage.
11. Check class imbalance in classification problems.
12. Do not rely on accuracy alone for highly imbalanced datasets.
13. There is no universal preprocessing pipeline.
14. Good preprocessing should be driven by the dataset, problem, and algorithm.

---

# 38. What Comes Next?

After understanding Data Preprocessing, the next major topic is:

## Supervised Learning

Topics to study:

* What is Supervised Learning?
* Classification
* Regression
* Training Data
* Testing Data
* Validation Data
* Common Supervised Learning Algorithms
* Linear Regression
* Logistic Regression
* KNN
* Naive Bayes
* Decision Tree
* Random Forest
* SVM
