# Day 13 — Machine Learning Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: ML Type Identification

### Problem 1 — Supervised vs Unsupervised
Classify each scenario:
a) Predicting house prices from size, bedrooms, location → _________
b) Grouping customers into segments based on purchase history without labels → _________
c) Detecting spam emails from labeled examples → _________
d) Finding frequent itemsets in a supermarket transaction database → _________

**Solution:**
a) **Supervised** (regression — labeled price data)
b) **Unsupervised** (clustering — no labels)
c) **Supervised** (classification — labeled spam/ham)
d) **Unsupervised** (association rule mining — no labels)

---

### Problem 2 — Classification vs Regression
Identify each as classification or regression:
a) Predict temperature tomorrow → _________
b) Diagnose disease (yes/no) → _________
c) Estimate a house's sale price → _________
d) Identify handwritten digits (0-9) → _________

**Solution:**
a) Regression (continuous value)
b) Classification (binary discrete class)
c) Regression (continuous value)
d) Classification (10 discrete classes)

---

## Set 2: Overfitting & Underfitting Trace

### Problem 3 — Identify the Problem
Scenario A: Training accuracy = 99%, Test accuracy = 52%
Scenario B: Training accuracy = 62%, Test accuracy = 60%
Scenario C: Training accuracy = 93%, Test accuracy = 91%

**Solution:**
A: **Overfitting** — huge gap, model memorized training
B: **Underfitting** — both low, model too simple
C: **Good fit** — both high and close

---

### Problem 4 — Fixing Overfitting
A model is overfitting. Which approaches would help?
a) Use more training data ✓
b) Use a simpler model ✓
c) Add regularization ✓
d) Train for more epochs ✗ (would worsen overfitting)
e) Reduce model complexity ✓
f) Use cross-validation ✓

---

### Problem 5 — Dataset Split
A team has 5,000 labeled images. What's the recommended split?

**Solution:** 70-80% training (3500-4000), 10-15% validation (500-750), 10-15% test (500-750). Larger training set = better performance.

---

## Set 3: Evaluation Metrics Trace

### Problem 6 — Confusion Matrix Calculation
```
Actual: YES  YES  NO  YES  NO  NO
Pred:   YES  NO   NO  YES  YES NO
```
Calculate TP, TN, FP, FN.

**Solution:**
- TP: actual YES, predicted YES = items 1, 4 → **2**
- TN: actual NO, predicted NO = items 3, 6 → **2**
- FP: actual NO, predicted YES = item 5 → **1**
- FN: actual YES, predicted NO = item 2 → **1**

Accuracy = (2+2)/(2+2+1+1) = 4/6 = 0.67
Precision = 2/(2+1) = 2/3 = 0.67
Recall = 2/(2+1) = 2/3 = 0.67
F1 = 2×(0.67×0.67)/(0.67+0.67) = 0.67

---

### Problem 7 — Precision vs Recall
A medical test for a rare disease:
- 100 people have the disease
- Test identifies 80 as positive (60 truly have it, 20 are false positives)
- Test misses 40 people who actually have the disease

Calculate Precision and Recall.

**Solution:**
- TP = 60, FP = 20, FN = 40
- **Precision** = TP/(TP+FP) = 60/80 = **0.75** (75% of positive predictions are correct)
- **Recall** = TP/(TP+FN) = 60/100 = **0.60** (60% of actual positives found)

---

### Problem 8 — Metric Matching
Match metric to definition:
1. Accuracy → a. TP/(TP+FP)
2. Precision → b. (TP+TN)/(TP+TN+FP+FN)
3. Recall → c. 2×(P×R)/(P+R)
4. F1 → d. TP/(TP+FN)

**Solution:** 1-b, 2-a, 3-d, 4-c

---

## Set 4: Ensemble Learning Trace

### Problem 9 — Ensemble Classification
Classify each as ensemble or NOT ensemble:
a) Random Forest → _________
b) Lasso Regression → _________
c) AdaBoost → _________
d) Bagging with decision trees → _________
e) Gradient Boosting → _________
f) Ridge Regression → _________

**Solution:**
a) **Ensemble** ✓ (bagging + decision trees)
b) **NOT ensemble** ✗ (L1 regularization technique)
c) **Ensemble** ✓ (boosting)
d) **Ensemble** ✓ (bagging)
e) **Ensemble** ✓ (boosting)
f) **NOT ensemble** ✗ (L2 regularization)

---

### Problem 10 — Bagging vs Boosting
Describe the key difference between bagging and boosting.

**Solution:**
- **Bagging** (Bootstrap Aggregating): trains models in **parallel** on different bootstrap samples; averages predictions
- **Boosting**: trains models **sequentially**; each new model focuses on errors of previous ones

---

## Set 5: Algorithm Selection

### Problem 11 — Which Algorithm?
Which algorithm for each scenario?
a) Segment customers into 3 groups by purchasing behavior → _________
b) Predict if a loan applicant will default (yes/no) → _________
c) Find products frequently bought together → _________
d) Predict a stock price next week → _________

**Solution:**
a) k-Means clustering (unsupervised)
b) Logistic Regression or Decision Tree (classification)
c) Association rule mining (Apriori)
d) Linear Regression or time series model (regression)

---

### Problem 12 — Optimization
Which technique is used to iteratively minimize a model's cost function by updating parameters?

**Solution:** **Gradient Descent** — model optimization technique

---

## Common Exam Traps — ML

| Trap | Explanation |
|------|-------------|
| **Lasso = NOT ensemble** | Lasso is **regularization (L1)**, not ensemble learning |
| **Gradient descent = optimization** | Gradient descent is a **model optimization technique** (not ensemble) |
| **Precision vs Recall** | Precision = TP/(TP+FP); Recall = TP/(TP+FN) |
| **Overfitting** | Good on training, **poor on new data** |
| **Model development** | **Large dataset boosts performance**; training > test |
| **Data mining order** | Training → Testing → Evaluation → Deployment |
| **Unsupervised = no labels** | Clustering and association have no labeled data |
| **Accuracy ≠ Precision** | Accuracy = overall correctness; Precision = positive prediction quality |
| **Ensemble types** | Bagging, Boosting, Random Forest — Lasso and Ridge are NOT ensemble |
