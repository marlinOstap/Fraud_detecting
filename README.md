# 💳 Credit Card Fraud Detection

## 📌 Overview | Обзор

**EN:**
This project focuses on detecting fraudulent credit card transactions using machine learning techniques.
The goal is to identify rare fraudulent operations in a highly imbalanced dataset.

**RU:**
Проект направлен на выявление мошеннических операций с банковскими картами с использованием методов машинного обучения.
Цель состоит в том, чтобы идентифицировать редкие мошеннические транзакции в сильно несбалансированных данных.
---



## 📊 Dataset | Данные

**EN:**
The dataset contains anonymized credit card transactions with a severe class imbalance.

* Fraudulent transactions: **~0.17%**
* Features: PCA-transformed (`V1–V28`) + `Time` and `Amount`
Dataset is not included due to size limitations.

**RU:**
Датасет содержит анонимизированные транзакции по банковским картам с сильным дисбалансом классов.
* Мошеннические транзакции: **~0.17%**
* Признаки: PCA-преобразованные (`V1–V28`) + `Time` и `Amount`
Данные не включены в репозиторий из-за размера.

📥 Download / Скачать:
https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud



## ⚙️ Project Structure | Структура проекта

```
Fraud_detecting/
│
├── notebooks/
│   ├── feature selection.ipynb
│   └── fraud_detection_models.ipynb
│
├── data/ (not included / не включена)
├── README.md
└── requirements.txt
```


## 🔍 EDA | Анализ данных

**EN:**
* Dataset structure analysis
* Class imbalance analysis
* Feature distribution comparison
* Zero-amount transaction analysis

**RU:**
* Анализ структуры данных
* Анализ дисбаланса классов
* Сравнение распределений признаков
* Анализ транзакций с нулевой суммой



## 🧠 Models | Модели

* **Logistic Regression**
  * `class_weight='balanced'`

* **Random Forest**
  * `n_estimators=100`
  * `max_depth=10`



## 📈 Metrics | Метрики
* ROC-AUC
* Precision / Recall / F1-score
* Confusion Matrix



## 📊 Results | Результаты

**EN:**
Both models successfully detect fraud despite strong imbalance.

**RU:**
Обе модели успешно выявляют мошеннические операции несмотря на сильный дисбаланс.



## 🚀 How to Run | Как запустить

1. Download dataset 
2. Create `data/` folder / 
3. Place file / 
```
data/creditcard.csv
```

4. Run notebooks / Запустить ноутбуки:

```
feature selection.ipynb → fraud_detection_models.ipynb
```



## 🛠️ Tech Stack

* Python
* Pandas / NumPy
* Scikit-learn
* Matplotlib / Seaborn



## 💡 Key Takeaways | Выводы

**EN:**

* Fraud detection is a highly imbalanced problem
* Accuracy is not a reliable metric
* Recall and ROC-AUC are crucial

**RU:**

* Задача сильно несбалансирована (~0.17% мошеннических транзакций
* Поэтому accuracy не информативна
* В таких условиях важнее метрики, отражающие способность модели находить мошенников, такие как Recall и ROC-AUC
