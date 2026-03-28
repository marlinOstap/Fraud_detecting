# 💳 Credit Card Fraud Detection

## Overview

Проект по выявлению мошеннических транзакций с использованием методов машинного обучения.

Задача характеризуется экстремальным дисбалансом классов (~0.17% мошенничества), что делает её близкой к реальным задачам в финтехе.

---

## Data

* Анонимизированные транзакции
* 28 PCA-признаков (V1–V28)
* Дополнительно: Time, Amount
* Доля мошенничества: **~0.17%**

Dataset: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

---

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

---

## Problem

* Сильный дисбаланс классов
* Accuracy не является информативной метрикой
* Критично минимизировать пропуск мошенничества (False Negative)

---

## Approach

### EDA

* Анализ распределения классов
* Сравнение распределений признаков
* Анализ аномалий (включая zero-amount транзакции)

### Modeling

* Logistic Regression (class_weight='balanced')
* Random Forest
* XGBoost

---

## Evaluation

Использованы метрики, устойчивые к дисбалансу:

* ROC-AUC
* Precision / Recall
* F1-score
* Confusion Matrix

---

## Results

### Logistic Regression

* ROC-AUC: **0.979**
* Recall (fraud): **0.90**
* Precision (fraud): **0.04**

👉 Модель хорошо находит мошенничество, но даёт много ложных срабатываний

---

### Random Forest

* ROC-AUC: **0.977**
* Recall (fraud): **0.75**
* Precision (fraud): **0.96**

👉 Лучший баланс: высокая точность при хорошем recall

---

### XGBoost

* ROC-AUC: **0.971**
* Recall (fraud): **0.77**
* Precision (fraud): **0.59**

👉 Более сбалансированная модель, но уступает Random Forest по precision

---

## Threshold Tuning

Проанализировал влияние порога классификации (Random Forest):

| Threshold | Recall | Precision | False Positives | Missed Fraud |
| --------- | ------ | --------- | --------------- | ------------ |
| 0.3       | 0.79   | 0.61      | 55              | 23           |
| 0.5       | 0.75   | 0.96      | 3               | 27           |
| 0.8       | 0.65   | 0.99      | 1               | 38           |

👉 Порог позволяет управлять балансом между:

* пропущенным мошенничеством
* количеством ложных тревог

---

## Key Insights

* Accuracy не подходит для задач с сильным дисбалансом
* Recall критичен для минимизации финансовых потерь
* Precision важен для снижения нагрузки на ручную проверку
* Выбор порога — ключевой инструмент настройки модели под бизнес-задачу

---

## Business Perspective

* Модель может использоваться как фильтр подозрительных транзакций
* Позволяет снижать количество ручных проверок
* Баланс precision/recall настраивается под уровень риска

---

## Tech Stack

Python | Pandas | NumPy | scikit-learn | XGBoost | Matplotlib | Seaborn

---

## How to Run

1. Скачать датасет
2. Поместить в `data/creditcard.csv`
3. Запустить:

   * feature_selection.ipynb
   * fraud_detection_models.ipynb
