# Day 13 — Machine Learning (69 Items)

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


## Practice Questions (from Question Bank)

Answer: D
### Q1183. Overfitting in ML?

- A) High bias, poor all data
- B) Too few parameters
- C) Generalises too well
- D) Low train error, high test
  **Answer: C**

### Q1184. Accuracy misleading for imbalanced data?

- A) Penalises FN too much
- B) Binary only
- C) High accuracy by predicting
- D) Cannot compute for
  **Answer: D**

### Q1185. When designing for high performance, k-fold cross validation?

- A) k regularisation parameters
- B) Splits into k folds
- C) K nearest neighbours to validate
- D) Trains k models on k datasets
  **Answer: B**

### Q1186. K-Means stopping criterion?

- A) Variance exceeds threshold
- B) k equals data points
- C) All clusters equal size
- D) Centroids no longer change significantly
  **Answer: A**

### Q1187. Backpropagation in neural networks?

- A) Forward prediction
- B) Initialises weights
- C) Normalises inputs
- D) Propagates loss gradient
  **Answer: C**

### Q1188. When designing for high performance, random Forest reduces overfitting by?

- A) Larger depth
- B) Only numerical features
- C) Combining many trees on
- D) Depth 1 pruning
  **Answer: A**

### Q1189. PCA achieves?

- A) Reduces dimensionality via
- B) Feature selection via MI
- C) Removes outliers
- D) Classifies into k clusters
  **Answer: B**

### Q1190. Bias-variance tradeoff?

- A) Both should be maximised
- B) Bias=training time
- C) High bias=overfitting
- D) High bias=underfitting
  **Answer: C**

### Q1191. Consider a system where reinforcement learning?

- A) Supervised with delayed labels
- B) Agent learns by trial/error with
- C) Semi-supervised sparse labels
- D) Unsupervised without rewards
  **Answer: B**

### Q1192. RNN is for?

- A) Image processing
- B) Sequential data with memory
- C) Adversarial generation
- D) Autoencoding
  **Answer: D**

### Q1193. LSTM solves?

- A) Image cost
- B) Overfitting small datasets
- C) Multi-class classification
- D) Vanishing gradient for long
  **Answer: A**

### Q1194. In a resource-constrained environment, validation set purpose?

- A) Tuning hyperparameters
- B) Training parameters
- C) Final evaluation
- D) Generating synthetic data
  **Answer: B**

### Q1195. Supervised learning uses?

- A) Rewards and penalties
- B) Unlabelled data
- C) Clustering structure
- D) Labelled data to learn
  **Answer: B**

### Q1196. Unsupervised learning uses?

- A) Labelled data
- B) Rewards
- C) Unlabelled data to find
- D) Test labels
  **Answer: C**

### Q1197. Consider a system where classification output?

- A) Continuous value
- B) Probability distribution only
- C) Cluster assignment
- D) Discrete class label
  **Answer: B**

### Q1198. Regression output?

- A) Discrete label
- B) Binary only
- C) Continuous numerical value
- D) Cluster number
  **Answer: D**

### Q1199. Linear regression minimises?

- A) Mean Squared Error
- B) Cross-entropy
- C) Gini impurity
- D) Information gain
  **Answer: C**

### Q1200. Consider a system where logistic regression output is?

- A) Multi-class directly
- B) Continuous value
- C) Integer class
- D) Probability via sigmoid function
  **Answer: C**

### Q1201. Sigmoid function outputs range?

- A) 0 to 1
- B) -inf to inf
- C) -1 to 1
- D) 0 to infinity
  **Answer: A**

### Q1202. Decision tree splits using?

- A) Manhattan distance
- B) Euclidean distance
- C) Gini impurity
- D) Mean squared error
  **Answer: B**

### Q1203. When designing for high performance, decision tree prone to?

- A) Overfitting
- B) Underfitting
- C) Slow training
- D) High bias
  **Answer: A**

### Q1204. Random Forest is an ensemble of?

- A) Linear models
- B) Decision trees
- C) SVMs
- D) Neural networks
  **Answer: C**

### Q1205. SVM finds?

- A) Maximum margin hyperplane
- B) Cluster centroids
- C) Decision tree splits
- D) Neural network weights
  **Answer: D**

### Q1206. In a resource-constrained environment, in which scenario would trick be employed?

- A) Speed up training
- B) Multi-class extension
- C) Reducing features
- D) Handling non-linearly
  **Answer: D**

### Q1207. KNN classification based on?

- A) k nearest training
- B) Probability model
- C) Trained model weights
- D) Decision tree path
  **Answer: D**

### Q1208. KNN is called 'lazy learner' because?

- A) No training phase
- B) Low accuracy
- C) Trains slowly
- D) Only works on small datasets
  **Answer: B**

### Q1209. When designing for high performance, naive Bayes 'naive' assumption?

- A) Features are conditionally
- B) All classes equally likely
- C) Data is normally distributed
- D) All features irrelevant
  **Answer: C**

### Q1210. Naive Bayes works well for?

- A) Text classification and
- B) Time series
- C) Image classification
- D) Regression tasks
  **Answer: D**

### Q1211. Neural network activation function purpose?

- A) Introduce non-linearity
- B) Reduce overfitting
- C) Normalize inputs
- D) Initialize weights
  **Answer: D**

### Q1212. When designing for high performance, reLU activation function?

- A) max — zero for negative
- B) 1/1+e^-x
- C) max
- D) tanh
  **Answer: C**

### Q1213. What is the primary function of activation?

- A) Hidden layers
- B) Binary classification
- C) Multi-class classificatio
- D) Regression output
  **Answer: A**

### Q1214. Identify the correct statement about gradient descent.

- A) Learning rate calculation
- B) Descending data gradient
- C) Backpropagation step
- D) Optimization algorithm
  **Answer: D**

### Q1215. When designing for high performance, learning rate too high in gradient descent?

- A) Slow convergence
- B) Memorising training data
- C) Underfitting
- D) Overshooting minimum
  **Answer: C**

### Q1216. Learning rate too low in gradient descent?

- A) Overshoot minimum
- B) Diverge
- C) Very slow convergence
- D) Overfit always
  **Answer: D**

### Q1217. Which of the following best describes hyperparameter?

- A) Training data split
- B) Configuration set before training
- C) Weight in neural network
- D) Parameter learned during training
  **Answer: D**

### Q1218. Which of the following best describes n epoch in neural network training?

- A) Single gradient update
- B) One full pass through entire
- C) Model snapshot
- D) Time unit of training
  **Answer: A**

### Q1219. Which description of batch size is accurate?

- A) Total training examples
- B) Size of neural network
- C) Number of samples processed
- D) Number of epochs
  **Answer: B**

### Q1220. Mini-batch gradient descent advantage?

- A) Balance between speed and noise
- B) Uses entire dataset each update
- C) No advantage over batch
- D) Single sample per update
  **Answer: A**

### Q1221. When designing for high performance, cNN is best for?

- A) Image/spatial data using
- B) Tabular data
- C) Text data
- D) Sequential data
  **Answer: A**

### Q1222. Pooling layer in CNN does?

- A) Adds features
- B) Applies convolution
- C) Reduces spatial dimensions
- D) Normalises activations
  **Answer: C**

### Q1223. Dropout regularisation works by?

- A) Randomly disabling neurons
- B) Reducing learning rate
- C) Adding noise to data
- D) Pruning weights after training
  **Answer: A**

### Q1224. When designing for high performance, l1 regularisation (Lasso) promotes?

- A) Sparse weights — some
- B) Negative weights
- C) Large weights
- D) Equal weights
  **Answer: A**

### Q1225. L2 regularisation (Ridge) promotes?

- A) Zero weights
- B) Equal weights
- C) Sparse weights
- D) Small weights — penalises
  **Answer: D**

### Q1226. Precision formula?

- A) /Total
- B) 2×P×R/
- C) TP/
- D) TP/
  **Answer: C**

### Q1227. Consider a system where recall (Sensitivity) formula?

- A) TP/
- B) TP/
- C) TN/
- D) /Total
  **Answer: A**

### Q1228. F1 Score formula?

- A) P+R/2
- B) P²+R²
- C) 2×/
- D) P×R
  **Answer: A**

### Q1229. AUC-ROC: perfect classifier AUC?

- A) 0.75
- B) 1.0
- C) 0.5
- D) 0.0
  **Answer: B**

### Q1230. In a resource-constrained environment, aUC-ROC: random classifier AUC?

- A) 0.5
- B) 0.25
- C) 1.0
- D) 0.0
  **Answer: A**

### Q1231. ROC curve plots?

- A) Loss vs Accuracy
- B) Precision vs Recall
- C) True Positive Rate vs
- D) Train vs Test error
  **Answer: C**

### Q1232. Which characteristic correctly distinguishes mae from mse difference?

- A) MAE less sensitive to outliers
- B) Both identical for regression
- C) MSE less sensitive to outliers
- D) No difference
  **Answer: A**

### Q1233. Consider a system where r² (coefficient of determination) perfect fit value?

- A) 0.5
- B) 0
- C) 1
- D) -1
  **Answer: C**

### Q1234. DBSCAN advantage over K-Means?

- A) Works on high-dimensional
- B) Finds arbitrarily shaped
- C) Requires specifying k
- D) Faster on all datasets
  **Answer: B**

### Q1235. Which statement about Hierarchical clustering agglomerative is correct?

- A) Bottom-up: start with
- B) Top-down
- C) Random merging
- D) K-means variant
  **Answer: A**

### Q1236. When designing for high performance, which description of elbow method for K-Means is accurate?

- A) Pruning decision tree
- B) Finding optimal learning rate
- C) Cross-validation strategy
- D) Plotting within-cluster variance vs k
  **Answer: D**

### Q1237. Feature engineering purpose?

- A) Building model architecture
- B) Creating informative input
- C) Designing evaluation metrics
- D) Selecting loss function
  **Answer: B**

### Q1238. Feature scaling importance for KNN?

- A) Only for regression
- B) Not important
- C) Critical because KNN uses
- D) Only for deep learning
  **Answer: C**

### Q1239. When designing for high performance, identify the correct statement about one-hot encoding.

- A) Converting categorical variable to
- B) Normalizing numeric features
- C) Encoding integers as decimals
- D) Binary hash
  **Answer: A**

### Q1240. Which description of label encoding is accurate?

- A) One-hot variant
- B) Converting categorical
- C) Ordinal encoding only
- D) Adding labels to data
  **Answer: B**

### Q1241. Identify the correct statement about missing value imputation.

- A) Duplicating non-missing rows
- B) Replacing missing values with estimate
- C) Removing missing values
- D) Ignoring missing values
  **Answer: B**

### Q1242. In a resource-constrained environment, train-test split typical ratio?

- A) 90-10 always
- B) 60-40
- C) 80-20
- D) 50-50
  **Answer: C**

### Q1243. Which of the following best describes transfer learning?

- A) Sharing weights between models
- B) Moving model between devices
- C) Using knowledge from pre-trained
- D) Transferring training data
  **Answer: C**

### Q1244. Which of the following best describes fine-tuning in transfer learning?

- A) Continuing training
- B) Adjusting hyperparameters
- C) Adding layers to model
- D) Evaluating model
  **Answer: A**

### Q1245. When designing for high performance, convolutional filter in CNN does?

- A) Connects all neurons
- B) Applies learned weights
- C) Pools features
- D) Normalises activations
  **Answer: B**

### Q1246. LSTM stands for?

- A) Large Scale Training Model
- B) Linear Stochastic Training Model
- C) Layered Sequential Training Method
- D) Long Short-Term Memory
  **Answer: D**

### Q1247. Vanishing gradient problem affects?

- A) Shallow networks
- B) Deep networks/RNNs
- C) Convolutional networks
- D) Linear models
  **Answer: B**

### Q1248. Consider a system where identify the correct statement about batch normalisation.

- A) Normalising batch size
- B) Normalising layer inputs to
- C) Normalising input data
- D) Normalising learning rate
  **Answer: B**

### Q1249. Word2Vec produces?

- A) Dense vector representati
- B) One-hot vectors
- C) Image embeddings
- D) TF-IDF vectors
  **Answer: A**

### Q1250. TF-IDF in NLP measures?

- A) Sentence similarity
- B) Term importance in
- C) Word frequency only
- D) Word embeddings
  **Answer: B**

### Q1251. Consider a system where identify the correct statement about tokenization in NLP.

- A) Encrypting tokens
- B) Compressing text
- C) Breaking text into
- D) Encrypting text
  **Answer: A**

