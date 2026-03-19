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

It processes raw text data (headline + description), cleans it, and predicts the most relevant category among multiple classes.

---

## 🧠 Model Architecture

The model is built using:

* **Embedding Layer (128 dimensions)**
* **Bidirectional LSTM (64 units)**
* **Fully Connected Dense Layers**
* **Softmax Output Layer**

### 🔗 Pipeline

Text → Cleaning → Tokenization → Padding → LSTM → Prediction

---

## ⚙️ Technologies Used

* Python 🐍
* TensorFlow / Keras 🤖
* Scikit-learn 📊
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

* 🎯 **Accuracy:** XX%
* 🎯 **Top-3 Accuracy:** XX%
* 📊 Multi-class classification (Top categories)

---

## 🧪 Example Predictions

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
📁 project/
│── 📄 notebook.ipynb
│── 📄 improved_news_classifier.h5
│── 📄 improved_tokenizer.pkl
│── 📄 improved_label_encoder.pkl
│── 📄 confusion_matrix.png
│── 📄 training_history.png
│── 📄 README.md
```

---

## ▶️ How to Run

### 1. Clone repository

```bash
git clone https://github.com/your-username/news-classification.git
cd news-classification
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
🎓 Computer Science Student
💻 Web & AI Developer

---

## ⭐ Show your support

If you like this project:

⭐ Star the repository
🔁 Share it on LinkedIn
💬 Give feedback

---

## 📜 License

This project is licensed under the MIT License.
