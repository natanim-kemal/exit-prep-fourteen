# Day 13 — Machine Learning Complete Theory (6 Items)

## LO1: ML Fundamentals — Supervised vs Unsupervised

### 1.1 What is Machine Learning?
- ML: algorithms that improve performance through experience (data)
- System learns patterns from data without being explicitly programmed for every rule

### 1.2 ML Types (Exam Priority!)
| Type | Labeled Data? | Goal | Examples |
|------|:------------:|------|----------|
| **Supervised Learning** | **Yes** | Learn mapping from input to output | Classification, Regression |
| **Unsupervised Learning** | **No** | Discover hidden patterns/structure | Clustering, Association |
| **Reinforcement Learning** | No (rewards) | Learn optimal actions via rewards | Game AI, Robotics |
| **Transfer Learning** | Varies | Apply knowledge from one task to another | Pre-trained models |

**Supervised Learning**:
- Training data includes input-output pairs (labeled)
- **Classification**: predict discrete class (spam/not spam, dog/cat)
- **Regression**: predict continuous value (price, temperature)

**Unsupervised Learning**:
- Training data has **no labels**
- **Clustering**: group similar items (k-means, hierarchical)
- **Association**: find relationships between variables (market basket)

### 1.3 Reinforcement Learning
- Agent learns by interacting with environment
- Receives **rewards** or **punishments** for actions
- Goal: maximize cumulative reward
- **Q-learning**: popular RL algorithm

---

## LO2: Overfitting, Underfitting & Model Development

### 2.1 Overfitting (Exam Priority!)
- Model fits training data **too closely**
- **Captures noise** instead of underlying pattern
- Works **well on training data, poorly on new/unseen data**
- Causes: too complex model, too little training data, training too long

### 2.2 Underfitting
- Model is **too simple** to capture underlying structure
- Works **poorly on both training and test data**
- Causes: too simple model, insufficient features, wrong algorithm

### 2.3 Bias-Variance Tradeoff
- **Bias**: error from overly simplistic assumptions (underfitting)
- **Variance**: error from sensitivity to small fluctuations (overfitting)
- Goal: balance between bias and variance

### 2.4 Model Development Best Practices
| Practice | Correct | Incorrect |
|----------|---------|-----------|
| Dataset size | **Large dataset boosts performance** ✓ | Small dataset is fine |
| Train/Test split | **Training > Test set** (70-80% train) | Training < Test set |
| Overlap | **No overlap** between train and test | Fifty-fifty overlap ✗ |
| Focus | Focus on training data quality | More focus on test data ✗ |

### 2.5 Data Mining Process
**Training → Testing → Evaluation → Deployment**
1. Train model on training data
2. Test model on unseen test data
3. Evaluate performance using metrics
4. Deploy to production

---

## LO3: Evaluation Metrics

### 3.1 Confusion Matrix (for Classification)
```
              Actual Positive    Actual Negative
Predicted +        TP                FP
Predicted -        FN                TN
```

### 3.2 Key Metrics
| Metric | Formula | What it measures |
|--------|---------|-----------------|
| **Accuracy** | (TP+TN)/(TP+TN+FP+FN) | Overall correctness |
| **Precision** | TP/(TP+FP) | How many predicted positives are actually positive |
| **Recall** | TP/(TP+FN) | How many actual positives were found |
| **F1-Score** | 2×(P×R)/(P+R) | Harmonic mean of precision and recall |

### 3.3 Precision vs Recall (From Exam)
- **Precision**: genuine defective segments / total predicted as defective = TP/(TP+FP)
- **Recall**: genuine defective segments / total actual defective = TP/(TP+FN)

### 3.4 ROC & AUC
- **ROC curve**: plots TPR vs FPR at various thresholds
- **AUC**: area under ROC curve — higher = better model

---

## LO4: ML Algorithms

### 4.1 Common Supervised Algorithms
| Algorithm | Type | Description |
|-----------|------|-------------|
| **Linear Regression** | Regression | Models linear relationship |
| **Logistic Regression** | Classification | Binary classification (despite name) |
| **Decision Tree** | Both | Tree of decisions based on features |
| **k-NN** (k-Nearest Neighbors) | Both | Classifies based on nearest neighbors |
| **SVM** (Support Vector Machine) | Both | Finds optimal separating hyperplane |
| **Naive Bayes** | Classification | Based on Bayes' theorem with independence assumption |

### 4.2 Common Unsupervised Algorithms
| Algorithm | Type | Description |
|-----------|------|-------------|
| **k-Means** | Clustering | Partitions into k clusters based on distance |
| **Hierarchical Clustering** | Clustering | Builds tree of clusters |
| **PCA** (Principal Component Analysis) | Dimensionality Reduction | Reduces feature space |
| **Association Rule** | Association | Finds frequent itemsets (market basket) |

---

## LO5: Ensemble Learning & Optimization (Exam Priority!)

### 5.1 Ensemble Learning
Combines multiple models to improve performance

| Technique | Description | Type |
|-----------|-------------|------|
| **Bagging** | Train multiple models on different bootstrap samples, average predictions | Ensemble ✓ |
| **Boosting** | Train models sequentially, each focuses on previous errors | Ensemble ✓ |
| **Random Forest** | Ensemble of decision trees using bagging + random feature selection | Ensemble ✓ |
| **Lasso (L1 Regularization)** | Adds penalty = λ∑|wᵢ| to cost function — **NOT ensemble** | Regularization |

**Lasso is NOT a type of ensemble learning** — it's a regularization technique!

### 5.2 Gradient Descent
- **Model optimization technique** ✓
- Iteratively adjusts parameters to minimize cost function
- Variants: Batch GD, Stochastic GD (SGD), Mini-batch GD
- Learning rate controls step size

### 5.3 Regularization
| Technique | Description |
|-----------|-------------|
| **L1 (Lasso)** | Adds absolute value penalty; produces sparse models |
| **L2 (Ridge)** | Adds squared penalty; shrinks coefficients evenly |
| **Elastic Net** | Combines L1 and L2 |

---

## LO6: Association Rules & Big Data Analytics

### 6.1 Association Rule Mining
- Finds relationships between items in transactional data
- **Market Basket Analysis**: "people who buy X also buy Y"
- Key metrics: Support, Confidence, Lift
- **Apriori algorithm**: finds frequent itemsets

### 6.2 Association Rule Example (From AAU 2015)
"People who buy shoes also buy socks with 0.75 probability" → **Association rule** technique

---

## Exam-Style Q&A (From 10 Actual Model Exam Questions)

**Q1:** One of the following is a model optimization technique?
- a. Bagging
- b. Lasso
- c. Gradient boosting
- d. **Gradient descent** ✓

**Q2:** Model fits too closely to training data, works poorly on new data?
- a. **Overfitting** ✓
- b. Underfitting
- c. Underperforming
- d. Sweet spot

**Q3:** In software testing, genuine defective segments / total predicted as faulty = ?
- a. **Precision** ✓
- b. Recall
- c. F-measure
- d. Accuracy

**Q4:** Which is NOT a type of ensemble learning?
- a. Bagging
- b. **Lasso** ✓ (Lasso = regularization, not ensemble)
- c. Random forest
- d. Boosting

**Q5:** Which learning algorithm is for data without labels?
- a. Transfer learning
- b. Supervised learning
- c. **Unsupervised learning** ✓
- d. Reinforcement learning

**Q6:** True about ML model development?
- a. More focus on test data
- b. **Large dataset boosts performance** ✓
- c. 50/50 overlap train/test
- d. Training proportion < test

**Q7:** Correct data mining process?
- a. **Training → Testing → Evaluation → Deployment** ✓
- b. Evaluation → Training → Testing → Deployment
- c. Training → Testing → Deployment → Evaluation
- d. Training → Evaluation → Testing → Deployment

**Q8:** People who buy shoes also buy socks → which analytics technique?
- a. Regression Modeling
- b. Clustering algorithm
- c. Predictive modeling
- d. **Association rule** ✓

---

---

## Question Bank Study Notes

### Types
**Supervised**: labeled data (classification, regression). Spam detection = Classification. Demand forecasting = Time-Series/Regression. **Unsupervised**: unlabeled data (clustering, association). **Reinforcement**: learn from rewards (game playing, robotics).

### Algorithms
Classification: Logistic Regression, Decision Trees, Random Forest, SVM, k-NN. Regression: Linear, Polynomial, Ridge/Lasso. Clustering: k-Means, Hierarchical, DBSCAN.

### Evaluation
Classification: Accuracy, Precision, Recall, F1-Score, Confusion Matrix. Regression: MSE, MAE, R².

### Overfitting vs Underfitting
Overfitting: complex model, good on train/poor on test → regularize, more data. Underfitting: simple model, poor everywhere → increase complexity.

### Ensemble
Bagging (parallel — Random Forest) reduces variance. Boosting (sequential — AdaBoost, XGBoost) reduces bias.

### Key Concepts
Gradient Descent: minimize loss. Word2Vec: dense word embeddings. TF-IDF: term importance. Batch Normalization: normalize layer inputs. Association rules: {diapers → beer}. Time-series: ARIMA, LSTM for forecasting.


## Quick Reference — Blueprint LOs

| LO | Topic | Items |
|----|-------|-------|
| 1 | Supervised vs Unsupervised learning | — |
| 2 | Overfitting, underfitting, model development | — |
| 3 | Evaluation metrics (precision, recall, accuracy, F1) | — |
| 4 | ML algorithms (classification, regression, clustering) | — |
| 5 | Ensemble learning & gradient descent | — |
| 6 | Association rules | — |
| **Total** | | **6** |
