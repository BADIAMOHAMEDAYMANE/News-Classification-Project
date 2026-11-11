# 📰 News Category Classification using Deep Learning

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python\&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?logo=tensorflow\&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?logo=keras\&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?logo=scikit-learn\&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-NLP-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Project Overview

This project aims to classify news articles into categories using **Deep Learning (Bidirectional LSTM)**.

It processes raw text data (headline + description), cleans it, and predicts the most relevant category among **42 classes**.

---

## 🗂️ Dataset

* **News Category Dataset v3** (`News_Category_Dataset_v3.json`, HuffPost headlines)
* **209,527 articles** loaded, **209,287** after cleaning
* **42 imbalanced categories** (largest: POLITICS with 35,602 articles, ~17%)
* Stratified **80 / 20 split**: 167,429 training articles, **41,858 test articles**

---

## 🧠 Model Architecture

The model is built using:

* **Embedding Layer (128 dimensions)**
* **Bidirectional LSTM (64 units)**
* **Fully Connected Dense Layers** (64 → 32, with Dropout)
* **Softmax Output Layer** (42 classes)

Training: Adam (lr 0.001), batch size 128, up to 15 epochs, `class_weight='balanced'`, EarlyStopping (patience 5) and ReduceLROnPlateau (patience 2).

### 🔗 Pipeline

Text → Cleaning (URLs, mentions, digits, punctuation, NLTK stopwords) → Keras Tokenizer (15,000 words) → Padding (26 tokens) → BiLSTM → Prediction

---

## ⚙️ Technologies Used

* Python 🐍
* TensorFlow / Keras 🤖
* Scikit-learn 📊 (train/test split, class weights, metrics)
* NLTK 🧹
* Pandas & NumPy
* Matplotlib & Seaborn 📈

---

## 📊 Features

✅ Text preprocessing (cleaning, stopwords removal)
✅ Tokenization & padding
✅ Class balancing
✅ Bidirectional LSTM model
✅ Early stopping & learning rate reduction
✅ Accuracy & Top-3 accuracy
✅ Confusion matrix visualization
✅ Training history graphs
✅ Custom prediction function

---

## 🚀 Results

Evaluated on **41,858 held-out test articles** (42 categories):

| Metric | Value |
|---|---|
| 🎯 Top-1 accuracy | **45.4%** |
| 🎯 Top-3 accuracy | **69.0%** |

Baselines for context: random guess **2.4%** (1/42), always predicting the majority class (POLITICS) **~17%**.

Several categories overlap (e.g. *ARTS* / *ARTS & CULTURE* / *CULTURE & ARTS*, *WORLDPOST* / *WORLD NEWS*), which is why top-3 accuracy is reported alongside top-1.

---

## 🧪 Example Prediction (illustrative output format)

```bash
Input:
"Lakers defeat Celtics in NBA Finals"

Prediction:
1. SPORTS (92%)
2. ENTERTAINMENT (5%)
3. POLITICS (3%)
```

---

## 📂 Project Structure

```
📁 News-Classification-Project/
│── 📄 News_Classification_Project.ipynb   # full pipeline (data → model → evaluation)
│── 📄 requirements.txt
│── 📄 README.md
```

Files generated when the notebook runs (not versioned): `improved_news_classifier.h5`, `improved_tokenizer.pkl`, `improved_label_encoder.pkl`, `confusion_matrix.png`, `training_history.png`.

---

## ▶️ How to Run

### 1. Clone repository

```bash
git clone https://github.com/BADIAMOHAMEDAYMANE/News-Classification-Project.git
cd News-Classification-Project
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run notebook

```bash
jupyter notebook
```

---

## 💡 Future Improvements

* 🔥 Use **BERT / Transformers**
* 🔥 Deploy as API (Flask / FastAPI)
* 🔥 Add web interface (React)
* 🔥 Hyperparameter tuning

---

## 👨‍💻 Author

**Mohamed Aymane Badia**
🎓 5th-year AI & Data Science engineering student (EMSI)
💻 Machine Learning & Web Developer

---

## ⭐ Show your support

If you like this project:

⭐ Star the repository
🔁 Share it on LinkedIn
💬 Give feedback

---

## 📜 License

This project is licensed under the MIT License.
