# Twitter Named Entity Recognition (NER) Project

## 🌐 Project Overview

This project aims to identify Named Entities from Twitter text using both classical and deep learning models. Named Entity Recognition (NER) is the task of identifying entities like names of people, locations, companies, etc., in unstructured text. This is particularly useful in social media analytics, where traditional cues like hashtags are not always reliable.

We approach this using:

* A **BiLSTM + CRF** model
* A **BERT-based transformer** model
* An enhanced **BERT + Sigmoid Focal Loss** model with hyperparameter tuning

---

## 📝 Problem Statement

NER for tweets poses unique challenges due to informal language, abbreviations, and lack of structure. The goal is to extract named entities from tweet text formatted in CoNLL format using BIO tagging scheme.

**Real-world Application**: Helps in improving content moderation, real-time news tracking, and brand monitoring on Twitter.

---

## 📚 Dataset

* **Source**: CoNLL-style annotated Twitter data
* **Format**: Each line contains a token and its entity label using BIO scheme
* **Entity Labels**: `person`, `geo-loc`, `company`, `product`, `facility`, `tvshow`, `movie`, `sportsteam`, `musicartist`, `other`

---

## 📈 Exploratory Data Analysis (EDA)

* Initial statistics of entity distribution
* Entity imbalance observed: e.g., some entities like `tvshow` and `movie` have very few examples
* Visualization using bar plots (recommended improvement)

---

## 🚀 Models Implemented

### ✅ BiLSTM + CRF

* Used custom tokenizer and embeddings
* CRF captures label dependencies (e.g., `I-geo-loc` must follow `B-geo-loc`)
* Trained with categorical cross-entropy loss
* **Issue**: Failed to generalize beyond the 'O' class due to data sparsity and underfitting

### ✅ BERT-Based Model

* Used `bert-base-cased` with subword tokenization
* Fine-tuned with sparse categorical cross-entropy
* Better than BiLSTM-CRF but suffered from class imbalance

### ✅ BERT + Sigmoid Focal Loss (Best Performing)

* Designed to handle class imbalance better
* Applied `SigmoidFocalCrossEntropy` loss with custom masking logic
* Further improved with KerasTuner for hyperparameter tuning
* Final model showed improved recall and F1 for key entity classes like `geo-loc`, `person`, and `company`

---

## 📊 Model Evaluation

### Metrics Used:

* **Precision**, **Recall**, **F1-Score** per entity
* **SeqEval** for sequence labeling accuracy

### Highlights:

* **BiLSTM-CRF**: Very high accuracy due to predicting mostly 'O' class; poor F1 for entities
* **Vanilla BERT**: Slight improvement in recall for entities but very low precision
* **Focal Loss BERT (Tuned)**: Balanced improvement in entity extraction, especially for high-support classes like `geo-loc`, `person`, and `company`

---

## 📊 Hyperparameter Tuning

* Used **KerasTuner Hyperband**
* Tuned dropout and learning rate for focal loss BERT model
* Best val\_loss: \~0.068
* Training Time: \~6.5 hours for 8 trials

---

## 📄 Conclusion

* The **BiLSTM + CRF** model was ineffective due to underfitting and class imbalance
* The **Vanilla BERT** model provided better token-level predictions but struggled on rare classes
* The **Focal Loss BERT** with hyperparameter tuning yielded the best entity-wise performance
* There is still scope for improving rare entity recognition via data augmentation and model ensembles

---

## 📘 Future Improvements

* Incorporate entity frequency plots during EDA
* Test with models like **RoBERTa**, **SpanBERT**, or **FlairNER**
* Use confusion matrices and error heatmaps
* Implement data augmentation strategies for minority classes

---

## 👨‍💼 Author

**Veeranna Hanamashetti**
M.S. in Data Science and Machine Learning
18+ years of professional experience in engineering, consulting, and data science

---

## 🔗 Repository Structure (Suggested)

```
├── data/
├── notebooks/
│   └── Twitter_NER_Project_00.ipynb
├── models/
├── outputs/
├── README.md
└── requirements.txt
```

---

## 💼 License

This project is released under the [MIT License](LICENSE).

---

Feel free to ⭐️ this repo if you found it helpful!
