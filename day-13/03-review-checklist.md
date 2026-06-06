# Day 13 — Machine Learning Review Checklist

## Mastery Checklist

### LO1: Supervised vs Unsupervised
- [ ] **Supervised**: labeled data, classification (discrete) + regression (continuous)
- [ ] **Unsupervised**: no labels, clustering (group) + association (find rules)
- [ ] **Reinforcement**: rewards/punishments, Q-learning
- [ ] **Transfer**: apply knowledge from one task to another

### LO2: Overfitting, Underfitting & Model Dev
- [ ] **Overfitting**: good on training, poor on test (too complex, captures noise)
- [ ] **Underfitting**: poor on both (too simple)
- [ ] **Large dataset boosts performance** ✓
- [ ] Training set > Test set (70-80% train)
- [ ] No overlap between train and test
- [ ] Data mining: Train → Test → Evaluate → Deploy

### LO3: Evaluation Metrics
- [ ] **Accuracy**: (TP+TN)/(TP+TN+FP+FN) — overall correctness
- [ ] **Precision**: TP/(TP+FP) — how many predicted positives are real
- [ ] **Recall**: TP/(TP+FN) — how many real positives were found
- [ ] **F1**: 2×(P×R)/(P+R) — harmonic mean
- [ ] Confusion matrix: TP, TN, FP, FN

### LO4: ML Algorithms
- [ ] Classification: Logistic Regression, Decision Tree, SVM, k-NN, Naive Bayes
- [ ] Regression: Linear Regression
- [ ] Clustering: k-Means, Hierarchical
- [ ] Dimensionality reduction: PCA
- [ ] Association: Apriori (market basket)

### LO5: Ensemble & Optimization
- [ ] **Ensemble**: Bagging, Boosting, Random Forest
- [ ] **NOT Ensemble**: Lasso (L1 regularization), Ridge (L2)
- [ ] **Gradient Descent**: optimization technique (minimizes cost function)

### LO6: Association Rules
- [ ] Association rule: "people who buy X also buy Y"
- [ ] Market basket analysis, Apriori algorithm
- [ ] Metrics: Support, Confidence, Lift

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **Supervised** | "**S**upervised = **S**tudent with answer key (labels)" |
| **Unsupervised** | "**U**nsupervised = **U**nknown answers (no labels)" |
| **Precision** | "**P**recision = **P**ositive predictive value" |
| **Recall** | "**R**ecall = find **R**elevant positives" |
| **Overfitting** | "**O**nly training **f**its, test **f**ails" |
| **Underfitting** | "**U**nder = **U**nable to capture anything" |
| **Ensemble** | "**E**nsemble = **E**veryone together (multiple models)" |
| **Lasso NOT ensemble** | "**L**asso is **L**1, not **L**earner group" |
| **Gradient descent** | "**D**own the **G**radient = minimize **E**rror" |
| **Data mining order** | "**T**rain → **T**est → **E**valuate → **D**eploy" |

## 1-Page Cram Sheet

```
ML TYPES
════════
Supervised   → labeled data (classify, regress)
Unsupervised → no labels (cluster, associate)
Reinforcement → rewards/punishments

OVERFITTING: train ✓, test ✗ → simplify, regularize

METRICS
═══════
Accuracy  = (TP+TN) / total
Precision = TP / (TP+FP)
Recall    = TP / (TP+FN)
F1        = 2×P×R / (P+R)

ALGORITHMS
══════════
Supervised: Linear/Logistic Regression, Decision Tree,
            SVM, k-NN, Naive Bayes
Unsupervised: k-Means, PCA, Apriori

ENSEMBLE: Bagging, Boosting, Random Forest
NOT ENSEMBLE: Lasso (L1), Ridge (L2)

OPTIMIZATION: Gradient Descent

Association Rule: "X → Y" (market basket)

MODEL DEV: Large data ✓, No overlap ✓, Train > Test ✓
DATA MINING: Train → Test → Eval → Deploy
