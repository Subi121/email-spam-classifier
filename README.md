# 📧 Spam Email Detection using Naive Bayes

This project demonstrates a Machine Learning–based Spam Email Detection system that classifies emails as **Spam** or **Not Spam**. The project focuses on implementing the **Naive Bayes algorithm** along with text preprocessing and feature extraction techniques to identify and filter unwanted email messages.

## 🎯 Objective

- Build a spam email classifier using Naive Bayes
- Convert email text into numerical features using Bag of Words and TF-IDF
- Train and compare different Naive Bayes models
- Evaluate model performance using classification metrics

## 🤖 Models Used

### 1. Bag of Words + Multinomial Naive Bayes

Counts word frequency in emails and detects spam patterns based on word occurrence.

### 2. TF-IDF + Multinomial Naive Bayes

Assigns higher importance to meaningful words and lower importance to common words, improving classification performance.

### 3. TF-IDF + Gaussian Naive Bayes

Uses TF-IDF values as continuous features and applies Gaussian probability distribution for spam classification.

## ✨ Features

- Email text preprocessing
- Feature extraction using:
  - Bag of Words (BoW)
  - TF-IDF
- Spam classification using Naive Bayes
- Model performance evaluation

## 📊 Evaluation Metrics

The models are evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn

## 📂 Project Workflow

1. Load the dataset  
2. Preprocess email text  
3. Convert text into numerical features (BoW / TF-IDF)  
4. Train Naive Bayes models  
5. Evaluate model performance  

## 📁 Dataset

The project uses a spam email dataset containing labeled email messages categorized as spam or non-spam.

## 🚀 Run the Project

1. Install required libraries
2. Load the dataset
3. Run the Jupyter Notebook or Python script
4. Train and evaluate the models

## 📌 Use Cases

- Email spam filtering systems
- SMS spam detection
- Cybersecurity email monitoring
- Fraud and phishing detection

## 📈 Conclusion

Naive Bayes classifiers provide an efficient and lightweight solution for spam detection. Among the tested models, **TF-IDF + Multinomial Naive Bayes** achieved the best performance by effectively identifying important spam-related terms while reducing the impact of commonly used words.
