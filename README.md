# 📧 Spam Email Detection using Naive Bayes

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-orange)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-complete-brightgreen)

A Machine Learning–based spam email detection system that classifies emails as **Spam** or **Ham (Not Spam)** using Naive Bayes classifiers with Bag of Words and TF-IDF feature extraction.

---

## 🎯 Objective
* Build a spam email classifier using Naive Bayes
* Extract text features using BoW and TF-IDF
* Compare different Naive Bayes models
* Evaluate performance using Accuracy, Precision, Recall, and F1 Score

---

## 📁 Dataset
| Property | Value |
|---|---|
| File | `emails.csv` |
| Total records | 5,728 |
| Ham (non-spam) | 4,360 (76.1%) |
| Spam | 1,368 (23.9%) |
| Missing values | None |
| Train / Test split | 80% / 20% (`random_state=42`) |


---


## 🛠️ Technologies Used
* Python 3.13
* pandas
* NumPy
* scikit-learn
  * `CountVectorizer`, `TfidfVectorizer`
  * `MultinomialNB`, `GaussianNB`

---

## 📂 Project Structure
```bash
spam-detection/
├── emails.csv              
├── spam_detection.ipynb
├── requirements.txt
└── README.md
```

---

## 🚀 Setup & Run
```bash
git clone https://github.com/Subi121/email-spam-classifier.git
cd email-spam-classifier
pip install -r requirements.txt
jupyter notebook spam_detection.ipynb
```

---

## 📂 Workflow
1. Load dataset
2. Check for null values and inspect class distribution
3. Split into train (80%) and test (20%) sets
4. Convert text into numerical features (BoW / TF-IDF)
5. Train Naive Bayes models
6. Evaluate and compare model performance

---

## 🤖 Models
### 1. BoW + Multinomial NB
Uses `CountVectorizer` to convert text into word frequency vectors.

### 2. TF-IDF + Multinomial NB ⭐ Best Model
Uses TF-IDF features with Multinomial NB and achieves perfect Precision (1.0) — no legitimate email is ever wrongly flagged as spam.

### 3. TF-IDF + Gaussian NB
Uses Gaussian NB on TF-IDF features. Achieves higher Recall and F1 Score but lower Precision.

---

## 📊 Results
| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| BoW + Multinomial NB | 98.9% | 97.9% | 97.6% | 97.7% |
| **TF-IDF + Multinomial NB** ⭐ | 89.3% | **100.0%** | 57.6% | 73.1% |
| TF-IDF + Gaussian NB | 95.4% | 95.8% | 85.5% | 90.3% |

### Why Precision Matters
In spam filtering, a **false positive** (blocking a real email) is more harmful than a **false negative** (letting spam through).
A Precision of **1.0** means the model never incorrectly marks a legitimate email as spam — making it the safest choice for a real inbox filter.

---

## ✨ Features
* Spam email classification
* BoW and TF-IDF feature extraction
* Comparison of three Naive Bayes models
* Performance evaluation using four classification metrics

---

## 📌 Use Cases
* Email spam filtering
* SMS spam detection
* Phishing email detection
* Cybersecurity monitoring

---

## 🔭 Future Improvements
* Add text preprocessing (lowercasing, stemming, punctuation removal)
* Improve Recall using threshold tuning (`predict_proba`)
* Add confusion matrix visualization
* Compare with Logistic Regression and SVM

---

## 📈 Conclusion
This project compares three Naive Bayes models for spam detection on a dataset of 5,728 emails.
**TF-IDF + Multinomial NB** achieved perfect Precision (1.0), making it the most reliable model for avoiding false spam predictions and ensuring no legitimate email is ever lost.

---

## 📄 License
This project is licensed under the [MIT License](LICENSE).
