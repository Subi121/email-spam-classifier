# 📧 Spam Email Detection using Naive Bayes

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-orange)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-complete-brightgreen)

A Machine Learning–based spam email detection system that classifies emails as **Spam** or **Ham (Not Spam)** using the Naive Bayes algorithm with TF-IDF feature extraction.

---

## 🎯 Objective

- Build a spam email classifier using Naive Bayes
- Extract text features using TF-IDF (Term Frequency–Inverse Document Frequency)
- Train and compare Multinomial NB vs Gaussian NB models
- Evaluate model performance using classification metrics
- Understand why metric choice matters in imbalanced classification tasks

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

The dataset contains two columns: `text` (raw email content) and `spam` (binary label: `1` = spam, `0` = ham).

> **Note:** The dataset file `emails.csv` is not included in this repository. Place it in the project root before running the notebook.

---

## 🛠️ Technologies Used

- Python 3.13
- pandas
- NumPy
- scikit-learn
  - `TfidfVectorizer`
  - `MultinomialNB`, `GaussianNB`
  - `train_test_split`
  - `accuracy_score`, `precision_score`, `recall_score`, `f1_score`

---

## 📂 Project Structure

```
spam-detection/
├── emails.csv            # Dataset (not included — see Dataset section)
├── spam_detection.ipynb  # Main Jupyter Notebook
├── requirements.txt
└── README.md
```

---

## 🚀 Setup & Run

```bash
git clone https://github.com/your-username/spam-detection.git
cd spam-detection
pip install -r requirements.txt
jupyter notebook spam_detection.ipynb
```

**requirements.txt**
```
pandas
numpy
scikit-learn
jupyter
```

---

## 📂 Project Workflow

1. Load dataset (`emails.csv`)
2. Check for null values and drop any missing rows
3. Inspect class distribution (ham vs spam)
4. Split into train (80%) and test (20%) sets
5. Vectorize text using `TfidfVectorizer(stop_words='english')`
6. Train Multinomial NB and Gaussian NB models
7. Evaluate each model using Accuracy, Precision, Recall, and F1 Score
8. Compare results and select the best model

---

## 🤖 Models

### Model 1: TF-IDF + Multinomial Naive Bayes

Converts email text into TF-IDF weighted features and applies Multinomial NB, which is designed for discrete count-like data. This model is extremely conservative — it only flags an email as spam when it is very confident, leading to perfect Precision but poor Recall.

### Model 2: TF-IDF + Gaussian Naive Bayes

Uses the same TF-IDF features but applies Gaussian NB, which assumes a normal distribution over continuous values. While Gaussian NB is theoretically mismatched for sparse text features, it achieves better overall performance on this dataset by striking a more practical balance between catching spam and avoiding false positives.

> ⚠️ **Implementation note:** The original notebook labels Model 1 as "Bag of Words + Multinomial NB" but the code actually uses `TfidfVectorizer` for both models — not `CountVectorizer`. A true BoW model was not implemented. This is corrected in the description above.

---

## 📊 Results

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| TF-IDF + Multinomial NB | 89.3% | **100.0%** | 57.6% | 73.1% |
| TF-IDF + Gaussian NB | **95.4%** | 95.8% | **85.5%** | **90.3%** |

### Key observations

- **Multinomial NB** achieves perfect Precision (1.0) — every email it flags as spam genuinely is spam. However, its Recall of 57.6% means it misses over 40% of actual spam. In a real inbox filter, this means a large fraction of spam gets through.
- **Gaussian NB** outperforms on every other metric: higher Accuracy (+6.1%), better Recall (+27.9%), and a substantially higher F1 Score (+17.2%), making it the more effective model in practice.
- **Accuracy can be misleading** in this context. With 76% of emails being ham, a model that predicts everything as ham would score 76% accuracy while catching zero spam. Recall and F1 are the more meaningful metrics here.

### Best model: TF-IDF + Gaussian NB

Despite the theoretical mismatch between Gaussian NB and sparse TF-IDF features, it delivers the strongest real-world performance with 95.4% accuracy and 90.3% F1 Score.

---

## ✨ Features

- Null value detection and removal
- Class distribution analysis
- TF-IDF feature extraction with English stopword removal
- Comparison of two Naive Bayes variants
- Evaluation using four classification metrics
- Discussion of why accuracy alone is insufficient for imbalanced datasets

---

## 📌 Use Cases

- Email spam filtering (Gmail, Outlook, Yahoo Mail)
- SMS spam detection
- Phishing and fraud email detection
- Cybersecurity email monitoring

---

## 🔭 Future Improvements

- Implement true **Bag of Words** (`CountVectorizer`) as a separate baseline for fair comparison
- Add **text preprocessing**: lowercasing, punctuation removal, stemming/lemmatization
- Address class imbalance using SMOTE or class weighting
- Tune hyperparameters with `GridSearchCV`
- Add a confusion matrix visualization
- Benchmark against a deep learning baseline (e.g., BERT)

---

## 📈 Conclusion

This project compares Multinomial NB and Gaussian NB for spam email classification using TF-IDF features on a dataset of 5,728 emails. While Multinomial NB achieves perfect Precision, **TF-IDF + Gaussian NB is the recommended model**, outperforming it on Accuracy (95.4%), Recall (85.5%), and F1 Score (90.3%). The project also highlights why F1 Score is a more reliable evaluation metric than Accuracy alone for imbalanced classification tasks.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
