# Applied Data Science with Python — Supervised ML, Text Mining, Visualization, Unsupervised Learning, NLP, Networks

[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/supervised_learning_partI.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/supervised_learning_partII.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/4. Applied Text Mining in Python/sentiment_analysis.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/2 Applied Plotting, Charting & Data Representation in Python/basic_plotting.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/2 Applied Plotting, Charting & Data Representation in Python/advanced_plotting.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/2 Applied Plotting, Charting & Data Representation in Python/plotting_visualization.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/unsupervised_learning.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/classifier_evaluation.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/train_test_learner.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/knn_modeling.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/simple_classification.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/evaluation_modeling.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/supervised_modeling_I.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/3. Applied Machine Learning in Python/classifier_visualization.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/4. Applied Text Mining in Python/basic_nltk.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/4. Applied Text Mining in Python/working_with_text.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/4. Applied Text Mining in Python/regex_and_named_groups.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/4. Applied Text Mining in Python/visualizing_graphs_with_networkX.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/5. Applied Social Network Analysis in Python/loading_graphs_in_networkX.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/5. Applied Social Network Analysis in Python/graph_features.ipynb]
[Source: WORK/KNOWLEDGE/Programming/Applied Data Science with Python/5. Applied Social Network Analysis in Python/sentiment_analysis_network.ipynb]

Coursera Applied Data Science with Python specialization (University of Michigan) — scikit-learn supervised learning algorithms and text feature engineering patterns.

---

## Setup and Core Libraries

```python
import numpy as np, pandas as pd, matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import MinMaxScaler
```

- Always scale features before distance-based or kernel-based models (KNN, SVM, MLP)
- `scaler.fit_transform(X_train)` then `scaler.transform(X_test)` — never fit on test set
- `train_test_split(X, y, random_state=0)` for reproducibility

---

## Supervised Learning Algorithms

### K-Nearest Neighbors (KNN)

```python
from sklearn.neighbors import KNeighborsClassifier, KNeighborsRegressor
knn = KNeighborsClassifier(n_neighbors=5).fit(X_train_scaled, y_train)
knnreg = KNeighborsRegressor(n_neighbors=5).fit(X_train, y_train)
```

- **Low K** = complex model (high variance, low bias); **high K** = smoother (high bias, low variance)
- Regression metric: R² score via `.score(X_test, y_test)`
- Requires feature scaling; sensitive to irrelevant features
- No training phase; prediction cost O(n·d) per query

### Linear Regression

```python
from sklearn.linear_model import LinearRegression
linreg = LinearRegression().fit(X_train, y_train)
# linreg.coef_, linreg.intercept_
```

- `R²` on test set measures generalization; high train R², low test R² = overfitting

### Ridge Regression (L2)

```python
from sklearn.linear_model import Ridge
linridge = Ridge(alpha=20.0).fit(X_train_scaled, y_train)
```

- L2 penalty shrinks coefficients toward zero; does not zero them out
- Higher `alpha` = more regularization; all features retained but smaller weights
- Requires feature scaling to compare coefficient magnitudes

### Lasso Regression (L1)

```python
from sklearn.linear_model import Lasso
linlasso = Lasso(alpha=2.0, max_iter=10000).fit(X_train_scaled, y_train)
# np.sum(linlasso.coef_ != 0)  # count non-zero features
```

- L1 penalty drives coefficients to exactly zero → automatic feature selection
- Higher `alpha` = fewer features retained
- Preferred when many features suspected irrelevant

### Polynomial Features

```python
from sklearn.preprocessing import PolynomialFeatures
poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)
```

- Adds interaction terms and degree-n terms to feature matrix
- Combine with Ridge to avoid overfitting from polynomial explosion
- Sensitive to outliers

### Logistic Regression

```python
from sklearn.linear_model import LogisticRegression
clf = LogisticRegression(C=100).fit(X_train, y_train)
```

- `C` = inverse of regularization strength; lower C = more regularization
- Binary and multi-class (one-vs-rest)
- Output is a probability bounded 0–1

### Support Vector Machines

```python
from sklearn.svm import SVC, LinearSVC
# Linear SVM
clf = LinearSVC(C=1.0).fit(X_train, y_train)
# Kernelized SVM (RBF default)
clf = SVC(kernel='rbf', C=10, gamma=1.0).fit(X_train_scaled, y_train)
# Polynomial kernel
clf = SVC(kernel='poly', degree=3).fit(X_train, y_train)
```

- `C` = margin softness; high C = smaller margin, fewer violations, more complex boundary
- `gamma` (RBF/poly): high gamma = tighter fit around training points (overfitting risk)
- `LinearSVC` with M classes → M one-vs-rest classifiers; `.coef_` is M×d matrix
- **Must scale features** — SVM performance degrades severely on unscaled data

### Naive Bayes

```python
from sklearn.naive_bayes import GaussianNB
nbclf = GaussianNB().fit(X_train, y_train)
```

- Assumes feature independence within each class (often violated, still works)
- Very fast; good baseline for text classification
- GaussianNB for continuous features; BernoulliNB/MultinomialNB for text counts

### Decision Trees

```python
from sklearn.tree import DecisionTreeClassifier
clf = DecisionTreeClassifier(max_depth=4, min_samples_leaf=8, random_state=0).fit(X_train, y_train)
# clf.feature_importances_  # normalized importances
```

- Unlimited depth → memorizes training data (100% train accuracy, poor test)
- `max_depth` is the primary pruning parameter; `min_samples_leaf` prevents tiny splits
- Feature importances: sum to 1.0; useful for feature selection

### Random Forests

```python
from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier(n_estimators=10, max_features=8, random_state=0).fit(X_train, y_train)
```

- Trains many trees on bootstrap samples; averages predictions
- `max_features` per split (default: sqrt(n_features) for classification) controls tree diversity
- More robust to overfitting than single decision trees
- Feature importances averaged across trees

### Gradient Boosted Decision Trees (GBDT)

```python
from sklearn.ensemble import GradientBoostingClassifier
clf = GradientBoostingClassifier(learning_rate=0.1, max_depth=3, random_state=0).fit(X_train, y_train)
```

- Sequential ensemble: each tree corrects residuals of previous
- `learning_rate` and `n_estimators` trade off: lower lr needs more estimators
- `max_depth=3` typical default; shallower = faster, less overfitting
- Often best accuracy on tabular data; slow to train

### Multi-Layer Perceptron (Neural Net)

```python
from sklearn.neural_network import MLPClassifier, MLPRegressor
clf = MLPClassifier(hidden_layer_sizes=[100, 100], activation='tanh', alpha=5.0,
                    solver='lbfgs', random_state=0).fit(X_train_scaled, y_train)
```

- `hidden_layer_sizes` = list of units per layer, e.g. `[100, 100]` = 2 hidden layers
- Activation functions: `relu` (default), `tanh`, `logistic`
- `alpha` = L2 regularization; higher alpha = simpler boundary
- `solver='lbfgs'` for small datasets; `adam` for large
- **Must scale features** — MLP highly sensitive to feature magnitude

---

## Model Evaluation

### Cross-Validation

```python
from sklearn.model_selection import cross_val_score
cv_scores = cross_val_score(clf, X, y)  # default 3-fold
print('Mean CV score: {:.3f}'.format(np.mean(cv_scores)))
```

- When scaling is needed within CV: use `Pipeline` to avoid data leakage — do NOT scale entire dataset before CV split

### Validation Curve

```python
from sklearn.model_selection import validation_curve
train_scores, test_scores = validation_curve(SVC(), X, y,
    param_name='gamma', param_range=np.logspace(-3, 3, 4), cv=3)
```

- Plots train vs. CV score vs. hyperparameter value — diagnoses under/overfitting

---

## Text Feature Engineering (Sentiment Analysis)

Dataset: Amazon Mobile Reviews (binary: positive rating = 4–5 stars).

### CountVectorizer

```python
from sklearn.feature_extraction.text import CountVectorizer
vect = CountVectorizer().fit(X_train)
X_train_vectorized = vect.transform(X_train)
# sparse matrix: rows=documents, cols=vocabulary terms
```

- Bag-of-words; ignores word order
- Limitation: treats "not working" and "not an issue, phone is working" identically if negation splits across unigrams

### TF-IDF Vectorizer

```python
from sklearn.feature_extraction.text import TfidfVectorizer
vect = TfidfVectorizer(min_df=5).fit(X_train)
```

- Downweights common words (high document frequency) and upweights rare informative terms
- `min_df=5` removes words appearing in fewer than 5 documents (reduces noise)
- Often better AUC than raw counts on sentiment tasks

### N-Grams

```python
vect = CountVectorizer(min_df=5, ngram_range=(1,2)).fit(X_train)
```

- `ngram_range=(1,2)` adds bigrams alongside unigrams
- Fixes negation problem: "not working" becomes a single feature distinct from "working"
- Substantially increases feature space; `min_df` threshold critical to control size

### Model Choice for Text

- `LogisticRegression` with vectorized features is strong baseline
- AUC (`roc_auc_score`) preferred over accuracy for imbalanced sentiment data
- Inspect `.coef_` sorted indices against `feature_names` to identify diagnostic features

---

## Algorithm Comparison Summary

| Algorithm | Scaling needed | Interpretable | Key hyperparameter |
|---|---|---|---|
| KNN | Yes | No | n_neighbors (K) |
| Linear/Ridge/Lasso | Yes (Ridge/Lasso) | Yes (coef_) | alpha |
| Logistic Regression | Recommended | Yes (coef_) | C |
| Linear SVM | Yes | Yes (coef_) | C |
| Kernel SVM | Yes | No | C, gamma |
| Naive Bayes | No | Partial | var_smoothing |
| Decision Tree | No | Yes (tree viz) | max_depth |
| Random Forest | No | Feature imp. | n_estimators, max_features |
| GBDT | No | Feature imp. | learning_rate, max_depth |
| MLP | Yes | No | hidden_layer_sizes, alpha |

---

## Data Visualization (matplotlib)

### Architecture

matplotlib has two layers:
- **Scripting layer** (`plt.*`) — stateful convenience API; implicitly tracks current figure/axes
- **Artist layer** (`Figure`, `Axes`, `Canvas`) — explicit OO API; required for embedding in applications

```python
# Scripting layer
plt.plot(x, y, '-o')
ax = plt.gca()  # get current axes

# Artist layer (no display state)
from matplotlib.backends.backend_agg import FigureCanvasAgg
from matplotlib.figure import Figure
fig = Figure()
canvas = FigureCanvasAgg(fig)
ax = fig.add_subplot(111)
ax.plot(x, y, '.')
canvas.print_png('output.png')
```

### Core Chart Types

```python
# Scatter
plt.scatter(x, y, s=100, c=colors, label='group')
plt.legend(loc=4, frameon=False)

# Line
plt.plot(linear_data, '-o', exponential_data, '-o')
plt.gca().fill_between(range(n), y1, y2, facecolor='blue', alpha=0.25)

# Bar (side-by-side)
plt.bar(xvals, data1, width=0.3)
plt.bar([x+0.3 for x in xvals], data2, width=0.3, color='red')
# Stacked bar
plt.bar(xvals, data1, color='b')
plt.bar(xvals, data2, bottom=data1, color='r')
# Horizontal
plt.barh(xvals, data, height=0.3)
# With error bars
plt.bar(xvals, data, yerr=err_list)
```

### Subplots and Layouts

```python
# Simple subplot
plt.subplot(1, 2, 1)   # rows, cols, index (1-based)
# Shared axis
ax1 = plt.subplot(1, 2, 1)
ax2 = plt.subplot(1, 2, 2, sharey=ax1)

# Grid of axes
fig, axes = plt.subplots(3, 3, sharex=True, sharey=True)

# Unequal layouts with gridspec
import matplotlib.gridspec as gridspec
gspec = gridspec.GridSpec(3, 3)
top_hist = plt.subplot(gspec[0, 1:])
side_hist = plt.subplot(gspec[1:, 0])
main = plt.subplot(gspec[1:, 1:])
```

### Statistical Charts

```python
# Histogram
ax.hist(sample, bins=100)

# Box plot (shows median, IQR, whiskers at 1.5×IQR by default)
plt.boxplot([df['normal'], df['random'], df['gamma']])
plt.boxplot(data, whis='range')  # whiskers extend to data extremes

# Heatmap (2D histogram)
plt.hist2d(X, Y, bins=25)
plt.colorbar()
```

### Animations and Interactivity

```python
# Animation
import matplotlib.animation as animation
def update(curr):
    if curr == n: a.event_source.stop()
    plt.cla()
    plt.hist(x[:curr], bins=bins)
fig = plt.figure()
a = animation.FuncAnimation(fig, update, interval=100)

# Click interactivity
def onclick(event):
    plt.gca().set_title('Clicked at data ({:.2f}, {:.2f})'.format(event.xdata, event.ydata))
plt.gcf().canvas.mpl_connect('button_press_event', onclick)

# Pick events (click on data points)
plt.scatter(x, y, picker=5)  # 5px tolerance
def onpick(event):
    print(df.iloc[event.ind[0]])
plt.gcf().canvas.mpl_connect('pick_event', onpick)
```

---

## Classifier Evaluation (Extended)

### Baseline with DummyClassifier

```python
from sklearn.dummy import DummyClassifier
dummy = DummyClassifier(strategy='most_frequent').fit(X_train, y_train)
# Always predicts majority class — accuracy = class frequency
# Real classifier must beat this baseline; high accuracy on imbalanced data is misleading
```

### Confusion Matrix and Metrics

```python
from sklearn.metrics import confusion_matrix, classification_report
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

# Binary
confusion = confusion_matrix(y_test, y_pred)
# [[TN, FP], [FN, TP]]

# Accuracy = (TP+TN) / total  — misleading when classes are imbalanced
# Precision = TP / (TP+FP)   — fraction of positive predictions that are correct
# Recall    = TP / (TP+FN)   — fraction of actual positives caught (sensitivity)
# F1        = 2×P×R / (P+R)  — harmonic mean; favors balanced precision/recall

print(classification_report(y_test, y_pred, target_names=['neg', 'pos']))
```

### Precision-Recall Curve

```python
from sklearn.metrics import precision_recall_curve
precision, recall, thresholds = precision_recall_curve(y_test, y_scores)
# Use decision_function() or predict_proba()[:,1] for scores
# Plot precision vs. recall — trade-off controlled by threshold
# High-recall (detect most positives) vs. high-precision (avoid false alarms)
```

### ROC Curve and AUC

```python
from sklearn.metrics import roc_curve, auc
fpr, tpr, _ = roc_curve(y_test, y_scores)
roc_auc = auc(fpr, tpr)
# AUC = 1.0 → perfect; AUC = 0.5 → random (diagonal line)
# ROC is insensitive to class imbalance; useful when both FP and FN costs matter
```

### Multi-Class Evaluation

```python
# Micro-averaging: weight by instance count (dominated by large classes)
precision_score(y_test, y_pred, average='micro')
# Macro-averaging: weight classes equally (emphasizes small classes)
precision_score(y_test, y_pred, average='macro')
```

### GridSearchCV with Custom Scoring

```python
from sklearn.model_selection import GridSearchCV
grid = GridSearchCV(SVC(), param_grid={'gamma': [0.001, 0.01, 0.1, 1, 10]},
                    scoring='roc_auc')
grid.fit(X_train, y_train)
# Different scoring metrics select different optimal hyperparameters
# e.g., optimizing for recall finds more positives but at cost of precision
```

---

## Unsupervised Learning

### Dimensionality Reduction

```python
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA

X_norm = StandardScaler().fit_transform(X)
pca = PCA(n_components=2).fit(X_norm)
X_pca = pca.transform(X_norm)
# pca.components_: shape (n_components, n_features) — feature loadings
# Always normalize (zero mean, unit variance) before PCA
```

```python
from sklearn.manifold import MDS
mds = MDS(n_components=2)
X_mds = mds.fit_transform(X_norm)
# Preserves pairwise distances; non-linear; computationally expensive
```

```python
from sklearn.manifold import TSNE
tsne = TSNE(random_state=0)
X_tsne = tsne.fit_transform(X_norm)
# Non-linear manifold; excellent for visualization; perplexity parameter matters
# Cluster separation meaningful; distances between clusters are NOT meaningful
```

### Clustering

```python
from sklearn.cluster import KMeans
kmeans = KMeans(n_clusters=4, random_state=0).fit(X_norm)
labels = kmeans.labels_
# Always normalize before K-means; scale affects distance calculations
```

```python
from sklearn.cluster import AgglomerativeClustering
from scipy.cluster.hierarchy import ward, dendrogram
cls = AgglomerativeClustering(n_clusters=3).fit(X)
# Builds hierarchy bottom-up; no need to specify k in advance
# Ward linkage minimizes within-cluster variance
dendrogram(ward(X))  # visualize hierarchy with scipy
```

```python
from sklearn.cluster import DBSCAN
cls = DBSCAN(eps=2, min_samples=2).fit(X)
# eps: neighborhood radius; min_samples: core point threshold
# Labels noise points as -1 (no cluster assignment)
# Finds arbitrary-shaped clusters; automatically determines k
```

---

## NLP with NLTK

### Preprocessing Pipeline

```python
import nltk

# Tokenization
tokens = nltk.word_tokenize("Children shouldn't drink this.")
# → ['Children', 'should', "n't", 'drink', 'this', '.']
sentences = nltk.sent_tokenize(text)  # sentence boundary detection

# Stemming (aggressive; output not always a word)
porter = nltk.PorterStemmer()
stems = [porter.stem(t) for t in tokens]
# "listing" → "list", "running" → "run"

# Lemmatization (returns actual words; needs POS)
lemma = nltk.WordNetLemmatizer()
lemmas = [lemma.lemmatize(t) for t in tokens]

# Frequency distribution
dist = nltk.FreqDist(text_tokens)
freq_words = [w for w in dist.keys() if len(w) > 5 and dist[w] > 100]
```

### POS Tagging and Parsing

```python
tagged = nltk.pos_tag(tokens)
# [('Children', 'NNP'), ('should', 'MD'), ('drink', 'VB'), ...]
# NN=noun, VB=verb, JJ=adj, MD=modal, RB=adverb, NNP=proper noun

# Context-free grammar parsing
grammar = nltk.CFG.fromstring("""
    S -> NP VP
    VP -> V NP
    NP -> 'Alice' | 'Bob'
    V -> 'loves'
""")
parser = nltk.ChartParser(grammar)
trees = list(parser.parse_all(nltk.word_tokenize("Alice loves Bob")))
# POS tagging is context-sensitive: "Visiting aunts can be a nuisance"
# — "Visiting" is VBG (gerund), but context changes its parse role
```

### Regex for Text Extraction

```python
import re
tokens = text.split(' ')
mentions = [w for w in tokens if re.search('@[A-Za-z0-9_]+', w)]
hashtags = [w for w in tokens if w.startswith('#')]
```

---

## Social Network Analysis with NetworkX

### Graph Loading

```python
import networkx as nx

# From edge list
G = nx.read_adjlist('graph.txt', nodetype=int)
G = nx.read_edgelist('edges.txt', data=[('weight', int)])

# From adjacency matrix
G = nx.Graph(np.array([[0,1,1],[1,0,0],[1,0,0]]))

# From pandas DataFrame
G = nx.from_pandas_dataframe(df, 'source', 'target', edge_attr='weight')

# Directed / multigraph
G = nx.read_edgelist('data.txt', data=[('outcome', int), ('timestamp', float)],
                     create_using=nx.MultiDiGraph())
```

### Graph Analysis

```python
# Degree (number of edges per node)
degrees = dict(G.degree())
max_node = max(degrees, key=degrees.get)

# Clustering coefficient (fraction of neighbors that are also neighbors of each other)
clustering = nx.clustering(G)

# Link prediction features
pa = [(u, v, p) for u, v, p in nx.preferential_attachment(G, edges)]
common_nbrs = len(list(nx.common_neighbors(G, u, v)))
```

### Feature Matrix from Graph

```python
df = pd.DataFrame(index=G.nodes())
df['population'] = pd.Series(nx.get_node_attributes(G, 'population'))
df['clustering'] = pd.Series(nx.clustering(G))
df['degree'] = pd.Series(dict(G.degree()))

# Edge features
edf = pd.DataFrame(index=G.edges())
edf['weight'] = pd.Series(nx.get_edge_attributes(G, 'weight'))
edf['pref_attach'] = [p for _, _, p in nx.preferential_attachment(G, edf.index)]
edf['common_nbrs'] = edf.index.map(lambda e: len(list(nx.common_neighbors(G, e[0], e[1]))))
# This feature matrix feeds directly into sklearn classifiers for link prediction
```
