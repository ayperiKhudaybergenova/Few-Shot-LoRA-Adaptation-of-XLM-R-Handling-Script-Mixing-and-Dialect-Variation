# Few-Shot-LoRA-Adaptation-of-XLM-R-Handling-Script-Mixing-and-Dialect-Variation

## Overview
This repository demonstrates **few-shot adaptation of the multilingual transformer model XLM-R** using **LoRA (Low-Rank Adaptation), a Parameter-Efficient Fine-Tuning (PEFT) method**, 
to handle **script-mixed and dialectal social media text**. The approach allows fine-tuning on **low-resource languages** with **very limited annotated data**, while leveraging the knowledge of a large pretrained model.
The goal is to create a model capable of **predicting the language or script** in real-world, noisy social media posts.

---

## Features
- Supports **multiple languages and scripts** (Latin, Cyrillic, and mixed forms).  
- Handles **dialectal and non-standard text** common in social media.  
- **Parameter-efficient fine-tuning (PEFT) with LoRA** reduces computational requirements and prevents overfitting.  
- Few-shot learning setup suitable for **low-resource languages**.  
- Provides a **workflow from raw data to trained PEFT-adapted model and evaluation**.

---

## Dataset
The repository includes small datasets (≈400 examples per language/script) for few-shot experiments:

| Language | Script | File |
|----------|--------|------|
| English  | Latin  | `English_Latin_400.txt` |
| Kazakh   | Cyrillic | `Kazakh_Cyrillic_400.txt` |
| Uzbek    | Latin  | `Uzbek_Latin_400.txt` |
| Russian  | Cyrillic | `Russian_Cyrillic_400.txt` |
| Karakalpak | Cyrillic | `Karakalpak_Cyrillic_400.txt` |

**Notes:**  
- Data is preprocessed and tokenized for XLM-R.  
-  manually annotated **golden test set** for evaluation.  
-  This project uses the kaalin-python library for converting Kazakh Cyrillic text to Latin script.https://github.com/dontbeidle/kaalin-python
The dataset used here represents non-standard social media writing, where users often mix or modify spelling and transliteration rules. This means that the data does not reflect the official orthography of either Kazakh or Karakalpak. Although Kazakh and Karakalpak Cyrillic share many script similarities, they are not fully identical.However, it is valuable for studying real usage patterns on social platforms, as people commonly write in these hybrid forms.
---

## Workflow
1. **Data Preparation** – Organize, clean, and optionally convert scripts (using `kaalin`).  
2. **Tokenization** – Convert text into tokens suitable for XLM-R.  
3. **Dataset Formatting** – Prepare train/validation/test sets for PyTorch.  
4. **Load Pretrained Model** – Use XLM-R as the base multilingual model.  
5. **LoRA (PEFT) Adaptation** – Fine-tune only a small subset of model parameters using PEFT.  
6. **Training** – Train the LoRA-adapted model on few-shot data.  
7. **Evaluation** – Test on golden-labeled sets using accuracy/F1 metrics.  
8. **Save Model** – Store PEFT weights and tokenizer for future use.  
9. **Optional Analysis** – Review confusion matrices, language/script misclassifications.  

---

## Model
The model used in this project is **XLM-R (XLM-RoBERTa)**, a multilingual transformer pretrained on over 100 languages, adapted for few-shot learning using **LoRA (Low-Rank Adaptation), a Parameter-Efficient Fine-Tuning (PEFT) method**. This allows the model to handle **script-mixed and dialectal social media text** efficiently, updating only a small subset of parameters while leveraging the full multilingual knowledge of XLM-R.

---

## Requirements
- Python 3.9+  
- PyTorch  
- `transformers`  
- `datasets`  
- **`peft` (LoRA / Parameter-Efficient Fine-Tuning)**  
- `accelerate`  
- `kaalin` (optional for script conversion)  
- `scikit-learn`, `numpy`, `pandas`  
- `wandb` (optional for logging)  

---

## Installation
```bash
git clone https://github.com/ayperiKhudaybergenova/Few-Shot-LoRA-Adaptation-of-XLM-R-Handling-Script-Mixing-and-Dialect-Variation.git
cd Few-Shot-LoRA-Adaptation-of-XLM-R-Handling-Script-Mixing-and-Dialect-Variation
pip install -r requirements.txt


This project uses the kaalin-python library for converting Kazakh Cyrillic text to Latin script.https://github.com/dontbeidle/kaalin-python
The dataset used here represents non-standard social media writing, where users often mix or modify spelling and transliteration rules. This means that the data does not reflect the official orthography of either Kazakh or Karakalpak. Although Kazakh and Karakalpak Cyrillic share many script similarities, they are not fully identical.However, it is valuable for studying real usage patterns on social platforms, as people commonly write in these hybrid forms.
