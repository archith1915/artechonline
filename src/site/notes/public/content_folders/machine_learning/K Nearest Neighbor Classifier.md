---
{"dg-publish":true,"permalink":"/public/content-folders/machine-learning/k-nearest-neighbor-classifier/","dgShowToc":true}
---

# What is KNN Classifier?

K-Nearest Neighbors (KNN) is a **simple, instance-based supervised machine learning algorithm** used mainly for classification tasks (though it can also be used for regression). It classifies a new data point based on the majority class among its _k_ nearest neighbors in the training data.

# What Does It Do?

KNN predicts the class of a data point by looking at the closest _k_ data points in the training set and assigning the most common class among those neighbors to the new point.

For example, if _k = 3_ and among the 3 nearest neighbors, 2 belong to class A and 1 belongs to class B, then the new point is classified as class A.

# How Does KNN Work?

1. **Choose the number of neighbors (k):** Decide how many neighbors to consider for voting.
    
2. **Calculate distances:** For the new (test) data point, compute the distance between it and all the points in the training dataset. Common distance metrics include:
    
    - Euclidean distance (most common)
        
    - Manhattan distance
        
    - Minkowski distance
        
3. **Sort neighbors by distance:** Find the _k_ points in the training set that are closest to the test point.
    
4. **Voting:** Count the frequency of classes among the _k_ nearest neighbors.
    
5. **Assign class:** Assign the class label that appears most frequently among these neighbors to the test point.


# Why Use KNN?

- **Simplicity:** KNN is very straightforward to understand and implement.
    
- **Non-parametric:** It does not assume any underlying data distribution.
    
- **No training phase:** Unlike other models, KNN is a lazy learner — it does not build an explicit model during training but stores all training data and performs classification during prediction.
    
- **Effective for small datasets:** Works well when the training dataset is small and well-labeled.
    
- **Adaptability:** Can handle multi-class classification easily.


# When to Use KNN?

- When you have **labeled data** and want a **simple classification method**.
    
- When the **decision boundary is irregular or complex**, and you do not want to assume a specific model form.
    
- For **small to medium-sized datasets** (since KNN requires computing distance to all points, which can be slow on large datasets).
    
- When features are numeric and the notion of distance between points makes sense.
    
- When you want a **baseline model** to compare more complex algorithms against.


# Limitations of KNN

- **Computationally expensive at prediction time:** Because it needs to compute distances to all training points.
    
- **Curse of dimensionality:** Performance can degrade with very high-dimensional data.
    
- **Sensitive to irrelevant features and feature scaling:** Features should be normalized or standardized for better distance calculation.
    
- **Choosing k:** Selecting the right value of _k_ is critical — too small can lead to noisy predictions, too large can smooth out class boundaries too much.

# Mathematics Behind KNN

KNN is a distance-based algorithm that does not build an explicit model but makes predictions using the training data directly. It calculates the distance—commonly Euclidean—between the input point and all training points to find the K nearest neighbors. For classification, it predicts the class that appears most frequently among the neighbors. For regression, it predicts the average of the neighbors' values. The algorithm relies entirely on distance metrics and majority or average voting, without any optimization or learning phase.


#  Summary

| Aspect           | Description                                                                   |
| ---------------- | ----------------------------------------------------------------------------- |
| Algorithm type   | Supervised, instance-based, lazy learning                                     |
| Use case         | Classification (and regression with modifications)                            |
| Key parameter    | Number of neighbors (_k_)                                                     |
| Distance metrics | Euclidean, Manhattan, Minkowski, etc.                                         |
| Strengths        | Simple, effective on small datasets, no training                              |
| Weaknesses       | Slow for large datasets, sensitive to feature scaling and irrelevant features |

# Code

```python
from sklearn.datasets import load_iris

from sklearn.model_selection import train_test_split

from sklearn.neighbors import KNeighborsClassifier

from sklearn.metrics import accuracy_score, classification_report, confusion_matrix

  

X,y = load_iris(return_X_y = True)

X_train, X_test, y_train, y_test = train_test_split(X,y, test_size=0.3, random_state=42)

  

model = KNeighborsClassifier(n_neighbors = 3)

model.fit(X_train, y_train)

  

prediction = model.predict(X_test)

  

for i in range(len(prediction)):

  pred = prediction[i]

  actual = y_test[i]

  status = "Correct" if pred==actual else "Wrong"

  print(f"{i+1} - Predicted : {pred} - Actual : {actual} - {status}")

  

accuracy = accuracy_score(y_test, prediction)

report = classification_report(y_test, prediction)

matrix = confusion_matrix(y_test, prediction)

  

print("\n")

print(f"Accuracy : {accuracy*100}%")

print(f"Classification Report : \n{report}")

print(f"Confusion Matrix : \n{matrix}")
```

# Explanation

This code trains and evaluates a K-Nearest Neighbors (KNN) classifier on the Iris dataset. It splits the data into training and testing sets, fits the KNN model, makes predictions on test data, and then reports the results including accuracy, classification report, and confusion matrix.

## Step-by-Step Explanation

### 1. Importing Necessary Libraries

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix
```

- What: Imports the Iris dataset loader, train/test data splitter, KNN model, and metrics to evaluate performance.  
- Why: These are essential tools to load data, create models, split datasets, and assess results.

---

### 2. Loading the Dataset and Splitting

```python
X,y = load_iris(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X,y, test_size=0.3, random_state=42)
```

- What: Loads features and labels of the Iris dataset and splits it into training (70%) and testing (30%) sets.  
- Why: Splitting data allows testing the model on unseen data to evaluate its generalization ability.

---

### 3. Creating and Training the KNN Model

```python
model = KNeighborsClassifier(n_neighbors=3)
model.fit(X_train, y_train)
```

- What: Creates a KNN classifier with 3 nearest neighbors and trains it on the training data.  
- Why: Training allows the model to learn the relationship between features and labels to predict new samples.

---

### 4. Making Predictions

```python
prediction = model.predict(X_test)
```

- What: Predicts the class labels of the test set using the trained KNN model.  
- Why: To see how well the model performs on unseen data.

---

### 5. Comparing Predictions to Actual Values

```python
for i in range(len(prediction)):
  pred = prediction[i]
  actual = y_test[i]
  status = "Correct" if pred == actual else "Wrong"
  print(f"{i+1} - Predicted : {pred} - Actual : {actual} - {status}")
```

- What: Iterates over all predictions and prints each predicted label, actual label, and whether the prediction was correct.  
- Why: This provides a detailed, example-level insight into model performance.

---

### 6. Calculating Evaluation Metrics

```python
accuracy = accuracy_score(y_test, prediction)
report = classification_report(y_test, prediction)
matrix = confusion_matrix(y_test, prediction)

print("\n")
print(f"Accuracy : {accuracy*100}%")
print(f"Classification Report : \n{report}")
print(f"Confusion Matrix : \n{matrix}")
```

- What: Calculates the overall accuracy percentage, detailed classification metrics (precision, recall, f1-score), and the confusion matrix to analyze model performance.  
- Why: These metrics quantify how well the model classifies the test data, highlighting strengths and weaknesses.

---

## Why This Should Be Done

- Splitting data into training and testing sets helps validate model generalization.  
- KNN is a simple and intuitive classification algorithm useful for many problems.  
- Evaluating predictions individually helps debug and understand specific mistakes.  
- Accuracy gives a quick summary of model performance, while classification report and confusion matrix provide deeper insights.  
- Such evaluation is critical before deploying any machine learning model in real-world applications.
