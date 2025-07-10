---
{"dg-publish":true,"permalink":"/content-folders/machine-learning/naive-bayes-gaussian-nb/","dgShowToc":true}
---

# What is Naive Bayes Classifier?

Naive Bayes is a family of **probabilistic classifiers** based on applying Bayes' theorem with the **“naive” assumption** that features are conditionally independent given the class label. Despite this strong assumption, it often performs surprisingly well in practice.

**Gaussian Naive Bayes (GaussianNB)** is a variant of Naive Bayes used when the features are continuous and assumed to follow a **normal (Gaussian) distribution**.

# What Does GaussianNB Do?

GaussianNB models the likelihood of the features assuming each feature follows a Gaussian distribution per class. For a new data point, it calculates the posterior probability for each class using Bayes’ theorem and assigns the class with the highest posterior probability.

# How Does GaussianNB Work?

1. **Training:**
    
    - For each class, calculate the **mean (μ)** and **variance (σ²)** of each feature across training samples belonging to that class.
        
    - Calculate the **prior probability** of each class (the proportion of samples in each class).
        
2. **Prediction:**
    
    - For a new sample, compute the **likelihood** of each feature given a class using the Gaussian probability density function:
        
        where is the feature value, and are the mean and variance of the feature in class .
        
    - Multiply likelihoods of all features (due to independence assumption) to get the total likelihood for the class.
        
    - Multiply by the class prior .
        
    - Assign the class label with the highest **posterior probability**:


# Why Use GaussianNB?

- **Fast and simple:** Training and prediction are very efficient.
    
- **Works well with small datasets.**
    
- **Handles continuous data:** Unlike Multinomial or Bernoulli Naive Bayes which require categorical or binary features, GaussianNB works for continuous-valued features.
    
- **Robust to irrelevant features:** Because of the independence assumption, irrelevant features tend to cancel out.
    
- **Probabilistic output:** Gives class probabilities, not just labels, useful for decision making.


# When to Use GaussianNB?

- When you have **continuous features** that are approximately normally distributed.
    
- When you need a **quick baseline classifier**.
    
- When you want a **probabilistic model** that is interpretable.
    
- When working on problems like **medical diagnosis, spam detection, or text classification** (after feature engineering).
    
- When the dataset is relatively **small or medium-sized**.

# Limitations of GaussianNB

- **Strong independence assumption:** Features are rarely independent, which can limit accuracy.
    
- **Gaussian assumption:** Performance drops if features are not normally distributed.
    
- **Poor with highly correlated features:** Can mislead the classifier.
    
- **Zero probabilities:** If a feature value was never seen in training for a class, likelihood becomes zero (though this can be handled with smoothing).


# Mathematics Behind Naive Bayes (GaussianNB)

Naive Bayes uses Bayes’ Theorem to compute the probability of each class given the input features, under the assumption that features are conditionally independent. In the Gaussian variant, it assumes that the values of continuous features follow a normal distribution. The probability of each feature given the class is calculated using the Gaussian probability density function, and the class with the highest posterior probability is chosen. This probabilistic framework makes the algorithm fast and effective, especially for high-dimensional data.

# Summary

| Aspect           | Description                                                 |
| ---------------- | ----------------------------------------------------------- |
| Algorithm type   | Supervised, probabilistic classifier                        |
| Model assumption | Features independent; continuous features ~ Gaussian        |
| Key parameters   | Mean and variance of each feature per class                 |
| Strengths        | Fast, simple, works well on small datasets                  |
| Weaknesses       | Independence and Gaussian assumptions can limit performance |
| Output           | Class probabilities and predicted class                     |


# Code

```python
import pandas as pd

from sklearn.model_selection import train_test_split

from sklearn.naive_bayes import GaussianNB

from sklearn.metrics import classification_report, accuracy_score, confusion_matrix

  

data = pd.read_csv('/content/drive/MyDrive/data.csv')

X, y = data.iloc[:, :-1], data.iloc[:, -1]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

  

model = GaussianNB().fit(X_train, y_train)

y_pred = model.predict(X_test)

  

print(f"Accuracy: {accuracy_score(y_test, y_pred):.2f}")

print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))

print("Classification Report:\n", classification_report(y_test, y_pred, zero_division=0))
```


# Execution

This code trains and evaluates a Gaussian Naive Bayes classifier using a dataset loaded from a CSV file. It splits the data into training and testing sets, fits the model, makes predictions, and evaluates its performance using accuracy, confusion matrix, and classification report.


## Step-by-Step Explanation

### 1. Importing Necessary Libraries


```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import classification_report, accuracy_score, confusion_matrix
```

- What: Imports pandas for data handling, scikit-learn tools for model training, prediction, and evaluation.  
- Why: These libraries are required to load data, build the model, split the data, and measure performance.

---

### 2. Loading the Dataset and Splitting into Features and Labels

```python
data = pd.read_csv('/content/drive/MyDrive/data.csv')
X, y = data.iloc[:, :-1], data.iloc[:, -1]
```

- What: Reads the dataset from a CSV file. `X` contains all columns except the last (features), and `y` contains the last column (target/label).  
- Why: Separates data into input and output for supervised learning.

---

### 3. Splitting the Data into Training and Testing Sets

```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

- What: Splits the dataset into 80% training and 20% testing sets.  
- Why: To train the model on part of the data and evaluate it on unseen data to test generalization.

---

### 4. Training the Gaussian Naive Bayes Model

```python
model = GaussianNB().fit(X_train, y_train)
```

- What: Creates a Gaussian Naive Bayes model and trains it on the training data.  
- Why: GaussianNB is suitable for continuous features and assumes the features follow a Gaussian distribution.

---

### 5. Making Predictions on the Test Set

```python
y_pred = model.predict(X_test)
```

- What: Uses the trained model to predict the labels for the test set.  
- Why: To assess how well the model performs on unseen data.

---

### 6. Evaluating the Model Performance

```python
print(f"Accuracy: {accuracy_score(y_test, y_pred):.2f}")
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
print("Classification Report:\n", classification_report(y_test, y_pred, zero_division=0))
```

What: 
- Calculates and prints the accuracy score.
- Displays the confusion matrix showing the counts of true/false positives/negatives.
- Prints a detailed classification report with precision, recall, and F1-score.

Why:
- Accuracy gives an overall measure of correct predictions.
- Confusion matrix shows how predictions are distributed across classes.
- Classification report helps understand performance per class and handles any zero-division cases gracefully.

---

## Why This Should Be Done

- Gaussian Naive Bayes is a fast and effective classification algorithm, especially for normally distributed data.
- Splitting data helps validate the model’s generalization to new data.
- Evaluation metrics provide insight into both overall and class-wise performance.
- Using classification reports and confusion matrices helps detect any issues like class imbalance or misclassification.

