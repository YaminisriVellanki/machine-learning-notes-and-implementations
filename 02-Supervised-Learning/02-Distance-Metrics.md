# Distance Metrics for Machine Learning

---

## 1. What is a Distance Metric?

A **distance metric** measures how far apart or different two data points are.

In general:

* **Small distance → more similar**
* **Large distance → less similar**

Distance metrics are especially important in algorithms that compare data points directly.

### Common algorithms that use distance

* K-Nearest Neighbors (KNN)
* K-Means Clustering
* Hierarchical Clustering
* DBSCAN
* Some recommendation and similarity systems

### Simple example

Suppose:

```text
A = (2, 3)
B = (5, 7)
```

A distance metric tells us **how far A is from B**.

Different metrics can give different answers because they measure distance in different ways.

---

# 2. Distance vs Similarity

These concepts are related but work in opposite directions.

### Distance

Measures **how different** two points are.

```text
Small distance → Similar
Large distance → Different
```

### Similarity

Measures **how similar** two objects are.

```text
High similarity → Similar
Low similarity → Different
```

Examples:

| Concept    | Example                               |
| ---------- | ------------------------------------- |
| Distance   | Euclidean, Manhattan                  |
| Similarity | Cosine similarity, Jaccard similarity |

---

# 3. Euclidean Distance

## Definition

**Euclidean distance** is the straight-line distance between two points.

It is the distance we normally think of geometrically.

### Formula — 2 dimensions

For:

```text
A = (x₁, y₁)
B = (x₂, y₂)
```

$$
d(A,B)=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}
$$

### Example

```text
A = (2, 3)
B = (5, 7)
```

$$
d=\sqrt{(5-2)^2+(7-3)^2}
$$

$$
=\sqrt{9+16}
$$

$$
=5
$$

So the Euclidean distance is **5**.

### Intuition

Think of drawing a straight line between two points.

```text
A ●────────────● B
       5
```

### Used in

* KNN
* K-Means
* Clustering
* Numerical data

### Interview point

> **Euclidean distance measures the straight-line distance between two points.**

---

# 4. Manhattan Distance

## Definition

**Manhattan distance** is the sum of the absolute differences between coordinates.

It is also called **City Block Distance** or **Taxicab Distance**.

### Formula

$$
d(A,B)=|x_2-x_1|+|y_2-y_1|
$$

### Example

```text
A = (2, 3)
B = (5, 7)
```

$$
d=|5-2|+|7-3|
$$

$$
=3+4
$$

$$
=7
$$

### Intuition

Imagine moving through city streets where you can move only horizontally and vertically.

```text
A → → →
      ↓
      ↓
      ↓
      B
```

You cannot travel diagonally.

### Used in

* KNN
* Clustering
* Grid-like data
* Situations where movement is along separate dimensions

### Interview point

> **Manhattan distance is the sum of absolute differences between coordinates.**

---

# 5. Euclidean vs Manhattan

| Feature                  | Euclidean                          | Manhattan                   |
| ------------------------ | ---------------------------------- | --------------------------- |
| Meaning                  | Straight-line distance             | City-block distance         |
| Formula                  | Square root of squared differences | Sum of absolute differences |
| Movement                 | Can be diagonal                    | Horizontal/vertical         |
| Example A=(2,3), B=(5,7) | 5                                  | 7                           |
| Used in                  | KNN, clustering                    | KNN, clustering             |

### Easy memory trick

**Euclidean → Straight line**

**Manhattan → City blocks**

---

# 6. Minkowski Distance

## Definition

**Minkowski distance** is a generalized distance formula that includes both Manhattan and Euclidean distance as special cases.

### Formula

$$
d(A,B)=
\left(
\sum_{i=1}^{n}|x_i-y_i|^p
\right)^{1/p}
$$

The value of **p** determines the type of distance.

### Important cases

If:

```text
p = 1
```

→ Manhattan distance

If:

```text
p = 2
```

→ Euclidean distance

### Easy understanding

```text
Minkowski
   |
   ├── p = 1 → Manhattan
   |
   └── p = 2 → Euclidean
```

### Used in

* KNN
* Distance-based algorithms

### Interview point

> **Minkowski distance is a generalized distance metric where Manhattan and Euclidean are special cases.**

---

# 7. Chebyshev Distance

## Definition

**Chebyshev distance** is the maximum absolute difference between corresponding coordinates.

### Formula

$$
d(A,B)=\max_i(|x_i-y_i|)
$$

### Example

```text
A = (2, 3)
B = (5, 7)
```

Differences:

```text
|5 - 2| = 3
|7 - 3| = 4
```

Maximum difference:

```text
max(3, 4) = 4
```

Therefore:

**Chebyshev distance = 4**

### Interview point

> **Chebyshev distance considers only the largest coordinate difference.**

### Easy memory trick

**Chebyshev → Maximum difference**

---

# 8. Hamming Distance

## Definition

**Hamming distance** measures the number of positions at which two equal-length sequences are different.

It is commonly used for:

* Binary data
* Strings
* Categorical representations
* Error detection

### Example

```text
A = 10110
B = 10011
```

Compare:

```text
1 = 1  → same
0 = 0  → same
1 ≠ 0  → different
1 = 1  → same
0 ≠ 1  → different
```

Number of differences:

```text
2
```

Therefore:

**Hamming distance = 2**

### Important condition

The two sequences should have the **same length**.

### Interview point

> **Hamming distance counts the number of positions where two equal-length sequences differ.**

### Easy memory trick

**Hamming → Count different positions**

---

# 9. Levenshtein Distance

## Definition

**Levenshtein distance** measures the minimum number of **single-character edits** required to transform one string into another.

The three allowed operations are:

1. **Insertion**
2. **Deletion**
3. **Substitution**

### Example

```text
cat
cut
```

Change:

```text
a → u
```

Only one substitution is required.

Therefore:

**Levenshtein distance = 1**

### Another example

```text
cat
cats
```

Add:

```text
s
```

Therefore:

**Levenshtein distance = 1**

### Used in

* Spell checking
* Autocorrect
* Search engines
* Fuzzy matching
* Comparing names
* Text processing
* Duplicate detection

### Important difference

**Hamming distance:**

Counts different positions.

**Levenshtein distance:**

Counts the minimum edits required to transform one string into another.

### Interview point

> **Levenshtein distance measures the minimum number of insertions, deletions, and substitutions needed to transform one string into another.**

### Easy memory trick

**Levenshtein → String edits**

---

# 10. Jaccard Similarity

## Definition

**Jaccard similarity** measures how similar two sets are by comparing their **intersection with their union**.

### Formula

$$
J(A,B)=\frac{|A\cap B|}{|A\cup B|}
$$

Where:

* `A ∩ B` → elements common to both sets
* `A ∪ B` → all unique elements from both sets

### Example

```text
A = {apple, banana, mango}

B = {banana, mango, orange}
```

Common elements:

```text
A ∩ B = {banana, mango}
```

Number of common elements:

```text
2
```

Union:

```text
A ∪ B = {apple, banana, mango, orange}
```

Number of unique elements:

```text
4
```

Therefore:

$$
J(A,B)=\frac{2}{4}=0.5
$$

So:

**Jaccard similarity = 0.5**

### Range

```text
0 → No overlap
1 → Completely identical
```

### Used in

* Set comparison
* Text/document similarity
* Duplicate detection
* Recommendation systems
* Binary/set-based data
* Comparing collections of items

### Interview point

> **Jaccard similarity is the size of the intersection divided by the size of the union of two sets.**

### Easy memory trick

**Jaccard → Intersection / Union**

---

# 11. Cosine Similarity

## Definition

**Cosine similarity** measures the similarity between two vectors based on the **angle between them**, rather than their physical distance.

### Formula

$$
\text{Cosine Similarity}
=
\frac{A\cdot B}
{\|A\|\|B\|}
$$

Where:

* `A · B` = dot product
* `||A||` = magnitude of A
* `||B||` = magnitude of B

### Intuition

Imagine two arrows starting from the same point.

```text
       B
      /
     /
    / θ
   /______
  A
```

If the angle is small:

→ vectors are more similar.

If the angle is large:

→ vectors are less similar.

### Used in

* Text similarity
* Search engines
* Recommendation systems
* Document similarity
* High-dimensional data

### Interview point

> **Cosine similarity measures similarity based on the angle between two vectors.**

### Easy memory trick

**Cosine → Angle between vectors**

---

# 12. Jaccard vs Cosine Similarity

Both measure similarity, but they are not the same.

| Feature    | Jaccard                | Cosine                 |
| ---------- | ---------------------- | ---------------------- |
| Works with | Sets / binary presence | Vectors                |
| Main idea  | Intersection ÷ Union   | Angle between vectors  |
| Common use | Set similarity         | Text/vector similarity |
| Focus      | Shared elements        | Direction              |

### Easy memory

**Jaccard → Set overlap**

**Cosine → Vector angle**

---

# 13. Complete Distance Metrics Comparison

| Metric          | Main Idea                     | Typical Use            |
| --------------- | ----------------------------- | ---------------------- |
| **Euclidean**   | Straight-line distance        | KNN, clustering        |
| **Manhattan**   | Sum of absolute differences   | KNN, clustering        |
| **Minkowski**   | Generalized distance          | KNN                    |
| **Chebyshev**   | Maximum coordinate difference | Numerical data         |
| **Hamming**     | Number of different positions | Binary/string data     |
| **Levenshtein** | Minimum string edits          | Text/string comparison |
| **Jaccard**     | Intersection ÷ Union          | Set similarity         |
| **Cosine**      | Angle between vectors         | Text/recommendation    |

---

# 14. Why Feature Scaling Matters for Distance

This is **very important for interviews**.

Suppose we have:

```text
Age       = 20–60
Salary    = 20,000–2,00,000
```

Salary has much larger numerical values than age.

Distance-based algorithms may therefore give salary much more influence.

### Solution

Use **feature scaling**.

Common methods:

### Standardization

$$
z=\frac{x-\mu}{\sigma}
$$

Using:

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

### Important rule

For distance-based algorithms:

**Scaling is often important.**

Especially for:

* KNN
* K-Means
* SVM
* PCA

---

# 15. Why Distance Matters in KNN

KNN uses distance to find the **nearest training examples**.

Suppose:

```text
New point
   ↓
Calculate distance to training points
   ↓
Find K nearest points
   ↓
Classification → Majority vote
Regression → Average
```

Example:

```text
K = 3
```

Nearest points:

```text
Point 1 → Class A
Point 2 → Class A
Point 3 → Class B
```

Majority:

```text
A → 2
B → 1
```

Prediction:

```text
Class A
```

Therefore, choosing an appropriate distance metric can affect KNN predictions.

---

# 16. Distance in K-Means

K-Means also uses distance to determine which cluster a data point belongs to.

Basic idea:

```text
Data points
     ↓
Calculate distance to centroids
     ↓
Assign point to nearest centroid
     ↓
Update centroids
     ↓
Repeat
```

So distance is also an important part of clustering.

---

# 17. How to Choose a Distance Metric?

There is **no single distance metric that is always best**.

The choice depends on:

* Type of data
* Data representation
* Scale of features
* Algorithm
* Problem requirements

### General understanding

| Data situation                        | Possible metric |
| ------------------------------------- | --------------- |
| Numerical continuous data             | Euclidean       |
| Grid/city-block type movement         | Manhattan       |
| Generalized numerical distance        | Minkowski       |
| Maximum coordinate difference matters | Chebyshev       |
| Equal-length binary/string positions  | Hamming         |
| Text/string edit comparison           | Levenshtein     |
| Set overlap                           | Jaccard         |
| Text/vector direction                 | Cosine          |

---

# 18. Distance Metrics and Machine Learning Algorithms

| Algorithm               | Uses Distance/Similarity?                                                       |
| ----------------------- | ------------------------------------------------------------------------------- |
| KNN                     | Yes                                                                             |
| K-Means                 | Yes                                                                             |
| Hierarchical Clustering | Yes                                                                             |
| DBSCAN                  | Yes                                                                             |
| Decision Tree           | Not fundamentally distance-based                                                |
| Random Forest           | Not fundamentally distance-based                                                |
| Linear Regression       | Not distance-based                                                              |
| Logistic Regression     | Not fundamentally distance-based                                                |
| Naive Bayes             | Not distance-based                                                              |
| SVM                     | Uses similarity/kernel concepts, but not simply nearest-distance classification |

---

# 19. Common Mistakes

### Mistake 1: Thinking all distances are the same

They measure relationships differently.

### Mistake 2: Forgetting scaling

Large-scale features can dominate distance calculations.

### Mistake 3: Confusing Hamming and Levenshtein

**Hamming:**

Number of different positions.

**Levenshtein:**

Minimum insertions, deletions, and substitutions.

### Mistake 4: Confusing Jaccard and Cosine

**Jaccard:**

Intersection / Union.

**Cosine:**

Angle between vectors.

### Mistake 5: Thinking smaller similarity is better

For similarity:

```text
Higher → more similar
```

For distance:

```text
Lower → more similar
```

---

# 20. 📝 Interview Quick Revision

### What is a distance metric?

A mathematical measure used to determine how far or different two data points are.

### Euclidean distance?

Straight-line distance between two points.

### Manhattan distance?

Sum of absolute differences between coordinates.

### Minkowski distance?

A generalized distance metric where `p=1` gives Manhattan and `p=2` gives Euclidean.

### Chebyshev distance?

Maximum absolute difference between corresponding coordinates.

### Hamming distance?

Number of positions at which two equal-length sequences differ.

### Levenshtein distance?

Minimum number of insertions, deletions, and substitutions required to transform one string into another.

### Jaccard similarity?

Intersection divided by union.

### Cosine similarity?

Measures similarity based on the angle between two vectors.

### Why is scaling important for KNN?

Because KNN relies on distance, and features with larger numerical ranges can dominate the distance calculation.

### Which algorithms are strongly affected by feature scaling?

Distance/scale-sensitive algorithms such as:

* KNN
* K-Means
* SVM
* PCA

### What is the difference between distance and similarity?

Distance measures **difference**, while similarity measures **closeness/similarity**.

---

# 21. 🧠 Memory Map

```text
DISTANCE & SIMILARITY
│
├── Numerical Distance
│   ├── Euclidean → Straight line
│   ├── Manhattan → City blocks
│   ├── Minkowski → Generalized
│   └── Chebyshev → Maximum difference
│
├── String / Binary
│   ├── Hamming → Different positions
│   └── Levenshtein → String edits
│
└── Similarity
    ├── Jaccard → Intersection / Union
    └── Cosine → Angle between vectors
```

---

# 22. ⭐ Recruiter/Interview Focus

You **do not need to memorize every formula without understanding it**.

For interviews, be able to explain:

1. What the metric measures.
2. The basic formula.
3. A simple example.
4. Where it is used.
5. Difference between similar metrics.
6. Why scaling matters.
7. How distance is used in KNN.
8. How distance is used in clustering.

### The most important comparisons

```text
Euclidean
    ↓
Straight-line distance

Manhattan
    ↓
City-block distance

Minkowski
    ↓
Generalized distance

Chebyshev
    ↓
Maximum difference

Hamming
    ↓
Different positions

Levenshtein
    ↓
String edits

Jaccard
    ↓
Intersection / Union

Cosine
    ↓
Angle between vectors
```

