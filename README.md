# 🐦 Twitter Named Entity Recognition (NER) Project

This project focuses on Named Entity Recognition (NER) on noisy Twitter data using a combination of classical and transformer-based deep learning models. It compares traditional BiLSTM+CRF with BERT-based models and demonstrates the benefit of using Focal Loss and hyperparameter tuning for performance improvement.

---

## 📌 Project Goals

- Classify tokens in tweets into 10 fine-grained entity categories like `person`, `company`, `geo-location`, etc.
- Handle noisy, imbalanced data with robust modeling strategies.
- Compare multiple architectures for NER.
- Improve performance using Focal Loss and KerasTuner.

---

## 🧠 Models Compared

| Model Variant                | Description                            | Result Summary                                   |
|-----------------------------|----------------------------------------|--------------------------------------------------|
| **BiLSTM + CRF**            | Classical sequence model                | Poor performance; only learned the `O` class     |
| **BERT (untuned)**          | Pretrained BERT with CE loss           | Minimal learning of entities; low F1             |
| **BERT + Focal Loss**       | Tackled class imbalance                | Improved recall and F1 on key entities           |
| **Tuned BERT + Focal Loss** | With KerasTuner hyperparameter tuning  | **Best model** with F1-score **0.25 (micro)**    |

---

## 📂 Project Structure

