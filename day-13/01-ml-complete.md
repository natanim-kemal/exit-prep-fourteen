# Machine Learning — Study Notes

## 1. Types of Machine Learning

**Supervised Learning**: learns from labeled data (input-output pairs).
- **Goal**: predict output for new inputs
- **Examples**: classification (spam detection, image recognition), regression (price prediction)
- **Best for**: Email spam detection (Classification), demand forecasting (Time-Series/Regression)

**Unsupervised Learning**: discovers patterns from unlabeled data.
- **Goal**: find hidden structure in data
- **Examples**: clustering (customer segmentation), association rule mining, dimensionality reduction

**Semi-Supervised Learning**: combines small labeled data with large unlabeled data.

**Reinforcement Learning**: agent learns by interacting with environment, receiving rewards/penalties.
- **Goal**: maximize cumulative reward
- **Examples**: game playing (AlphaGo), robotics, autonomous driving

## 2. Key Algorithms

### Classification
- **Logistic Regression**: binary classification (despite name, it's for classification)
- **Decision Trees**: tree-like structure for decisions; easy to interpret but prone to overfitting
- **Random Forest**: ensemble of decision trees; reduces overfitting
- **SVM (Support Vector Machine)**: finds optimal hyperplane to separate classes
- **k-NN (k-Nearest Neighbors)**: classifies based on majority of k nearest neighbors

### Regression
- **Linear Regression**: models linear relationship between variables
- **Polynomial Regression**: models non-linear relationships
- **Ridge/Lasso Regression**: regularized linear regression to prevent overfitting

### Clustering
- **k-Means**: partitions data into k clusters; simple and fast
- **Hierarchical Clustering**: builds tree of clusters (agglomerative/divisive)
- **DBSCAN**: density-based clustering; handles noise

## 3. Model Evaluation Metrics

**For Classification**:
- **Accuracy**: (TP+TN)/(TP+TN+FP+FN) — overall correctness
- **Precision**: TP/(TP+FP) — how many positive predictions are correct
- **Recall (Sensitivity)**: TP/(TP+FN) — how many actual positives were found
- **F1-Score**: harmonic mean of precision and recall
- **Confusion Matrix**: TP, TN, FP, FN

**For Regression**:
- **MSE (Mean Squared Error)**: average of squared errors
- **MAE (Mean Absolute Error)**: average of absolute errors
- **R² (R-squared)**: proportion of variance explained

## 4. Overfitting & Underfitting

**Overfitting**: model performs well on training data but poorly on new data.
- **Causes**: too complex model, too many features, insufficient training data
- **Solutions**: regularization (L1/L2), more data, feature selection, cross-validation, early stopping

**Underfitting**: model performs poorly on both training and test data.
- **Causes**: too simple model, insufficient features
- **Solutions**: increase model complexity, add features, reduce regularization

**Bias-Variance Tradeoff**:
- **High bias** → underfitting (model too simple)
- **High variance** → overfitting (model too complex)

## 5. Ensemble Learning

Combines multiple models to produce better results.

**Bagging (Bootstrap Aggregating)**: train models in parallel on different data subsets; reduces variance (Random Forest).

**Boosting**: train models sequentially, each correcting previous errors; reduces bias (AdaBoost, Gradient Boosting, XGBoost).

**Stacking**: combine different model types using a meta-learner.

## 6. Key Concepts

**Gradient Descent**: iterative optimization algorithm to minimize loss function. Variants: Batch GD, Stochastic GD (SGD), Mini-batch GD.

**Feature Engineering**: creating/selecting informative features from raw data.

**Word2Vec**: produces dense vector representations of words (word embeddings) — captures semantic meaning.

**TF-IDF**: measures term importance in a document relative to a corpus; widely used for text feature extraction.

**Normalization/Batch Normalization**: normalizing layer inputs to stabilize and accelerate training.

**Train/Test Split**: typically 70-80% training, 20-30% testing. Never overlap train/test data.

## 7. Association Rule Mining

**Technique**: finds relationships between items in large datasets (market basket analysis).

**Metrics**: Support (frequency), Confidence (conditional probability), Lift (strength beyond random).

**Example**: {diapers} → {beer} — people who buy diapers are likely to buy beer.

## 8. Time-Series Forecasting

Predicts future values based on historical time-ordered data. Used for demand forecasting, stock prices, weather prediction.

**Methods**: ARIMA, SARIMA, Exponential Smoothing, LSTM (deep learning).
