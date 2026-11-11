# 📰 News Category Classification — BiLSTM vs TF-IDF baseline

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python\&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?logo=tensorflow\&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-red?logo=keras\&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?logo=scikit-learn\&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-NLP-green)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Project Overview

This project classifies news articles into **42 categories** from their headline and short description.

It compares a **Deep Learning model (Bidirectional LSTM)** with a classic **TF-IDF + linear SVM baseline**, and studies the effect of class weighting on a strongly imbalanced dataset.

---

## 🗂️ Dataset

* **News Category Dataset v3** (`News_Category_Dataset_v3.json`, HuffPost headlines)
* **209,527 articles** loaded (rows with an empty title or text are removed during cleaning)
* **42 imbalanced categories** (largest: POLITICS with 35,602 articles, ~17%)
* Stratified **80 / 20 split** (`random_state=42`): **41,889 test articles**

---

## 🧠 Model Architecture

The model is built using:

* **Embedding Layer (128 dimensions)**
* **Bidirectional LSTM (64 units)**
* **Fully Connected Dense Layers** (64 → 32, with Dropout)
* **Softmax Output Layer** (42 classes)

Training: Adam (lr 0.001), batch size 128, up to 15 epochs, **softened class weights** (square root of the inverse class frequency), EarlyStopping on `val_loss` (patience 3, best weights restored) and ReduceLROnPlateau (patience 2).

### 📏 Baseline

`TfidfVectorizer` (unigrams + bigrams, `min_df=2`, sublinear TF) + `LinearSVC` (C = 0.5), trained on the same cleaned texts and the same split.

### 🔗 Pipeline

Text → Cleaning (URLs, mentions, digits, punctuation, NLTK stopwords) → Keras Tokenizer (15,000 words) → Padding (90th-percentile length) → BiLSTM → Prediction

---

## ⚙️ Technologies Used

* Python 🐍
* TensorFlow / Keras 🤖
* Scikit-learn 📊 (TF-IDF + LinearSVC baseline, train/test split, metrics)
* NLTK 🧹
* Pandas & NumPy
* Matplotlib & Seaborn 📈

---

## 📊 Features

✅ Text preprocessing (cleaning, stopwords removal)
✅ Tokenization & padding
✅ Softened class weights (imbalanced classes)
✅ Bidirectional LSTM model
✅ Early stopping & learning rate reduction
✅ Accuracy & Top-3 accuracy
✅ Confusion matrix visualization
✅ Training history graphs
✅ Custom prediction function
✅ TF-IDF + LinearSVC baseline for comparison

---

## 🚀 Results

Evaluated on **41,889 held-out test articles** (42 categories):

| Model | Top-1 accuracy | Top-3 accuracy | Macro F1 |
|---|---|---|---|
| **TF-IDF + LinearSVC (baseline)** | **63.5%** | **83.3%** | **0.503** |
| BiLSTM — softened class weights | 55.4% | 74.3% | 0.405 |
| BiLSTM — `class_weight='balanced'` (first version) | 36.7% | 66.5% | 0.342 |

**What the experiments show**

* **Fully balanced class weights hurt the large classes**: with `class_weight='balanced'`, the POLITICS recall dropped to **6%** (the model almost never predicted it). Softening the weights (square root) brought it back to **70%** and raised accuracy from 36.7% to 55.4%.
* **The simple baseline beats the BiLSTM** by 8 points: on short texts (headline + one sentence) where vocabulary is very discriminative, TF-IDF n-grams with a linear model remain very strong, while the BiLSTM starts overfitting after ~5 epochs.

Baselines for context: random guess **2.4%** (1/42), always predicting the majority class (POLITICS) **~17%**.

Several categories overlap (e.g. *ARTS* / *ARTS & CULTURE* / *CULTURE & ARTS*, *WORLDPOST* / *WORLD NEWS*), which is why top-3 accuracy is reported alongside top-1.

---

## 🧪 Example Predictions (BiLSTM, real outputs)

```
📰 Lakers defeat Celtics in NBA Finals
   1. SPORTS          : 98.90%
   2. WOMEN           :  0.59%
   3. COMEDY          :  0.20%

📰 New smartphone released by Apple
   1. TECH            : 89.50%
   2. BUSINESS        :  2.62%
   3. COMEDY          :  1.86%

📰 President announces economic reform
   1. WORLD NEWS      : 28.19%
   2. THE WORLDPOST   : 26.18%
   3. POLITICS        : 13.41%
```

The last example shows the overlap between news categories: the right answer (POLITICS) is only in the top 3.

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

### 3. Run the notebook

The notebook is designed for **Google Colab** (GPU T4): open it with the "Open in Colab" badge, run all cells and upload `News_Category_Dataset_v3.json` (or the Kaggle `.zip` archive) when prompted.

---

## 💡 Future Improvements

* 🔥 Fine-tune a **Transformer** (DistilBERT) and compare it with the TF-IDF baseline
* 🔥 Merge overlapping categories (e.g. *WORLDPOST* / *THE WORLDPOST*) and measure the impact
* 🔥 Hyperparameter tuning (vocabulary size, regularization of the SVM)
* 🔥 Deploy the best model as an API (Flask / FastAPI)

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
