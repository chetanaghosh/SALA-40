# Tokenization Efficiency Analysis for Bengali and Hindi Across Multilingual Language Models

## Overview

This project investigates how different multilingual language models tokenize native-script and romanized text in Bengali and Hindi. The notebook compares tokenization behaviour across:

* GPT tokenizer (`cl100k_base`)
* MuRIL (`google/muril-base-cased`)
* mBERT (`bert-base-multilingual-cased`)

The study uses sentence pairs from the AI4Bharat **Bhasha-Abhijnaanam** dataset and evaluates:

* Token counts for native vs romanized text
* Script Sensitivity Ratio (SSR)
* Native Script Load (NSL)
* Cross-model tokenization efficiency
* Visualization through heatmaps and comparative bar charts

This analysis is particularly relevant for:

* Computational linguistics
* Multilingual NLP
* Indic language processing
* Romanization studies
* Tokenization efficiency research

---

# Research Objective

The notebook explores whether multilingual models process native scripts more efficiently than romanized forms for Bengali and Hindi.

Key research questions include:

1. Do multilingual models tokenize native Indic scripts more efficiently?
2. How much token inflation occurs after romanization?
3. Are language-specific models such as MuRIL more robust to Indic scripts than general multilingual models?
4. How do GPT-family tokenizers compare with multilingual BERT tokenizers on Indic languages?

---

# Dataset

The notebook uses:

* **Dataset:** AI4Bharat Bhasha-Abhijnaanam
* **Source:** Hugging Face Datasets

The dataset contains:

* Native-script sentences
* Romanized equivalents
* Language labels

Languages used in this notebook:

* Bengali (Bangla)
* Hindi

---

# Models Used

## 1. GPT Tokenizer

Uses OpenAI's `cl100k_base` tokenizer via `tiktoken`.

Purpose:

* Measures tokenization behaviour similar to GPT-family models.

---

## 2. MuRIL

Model:

* `google/muril-base-cased`

Purpose:

* Indic-focused multilingual representation model.
* Expected to handle Indic scripts more efficiently.

---

## 3. mBERT

Model:

* `bert-base-multilingual-cased`

Purpose:

* General multilingual baseline.

---

# Methodology

## Step 1 — Load Dataset

The notebook loads the dataset using Hugging Face:

```python
from datasets import load_dataset

dataset = load_dataset("ai4bharat/Bhasha-Abhijnaanam")
```

---

## Step 2 — Filter Languages

The notebook extracts:

* Bengali samples
* Hindi samples

---

## Step 3 — Clean Data

Entries with missing native or romanized text are removed.

---

## Step 4 — Random Sampling

The notebook randomly selects:

* 200 Bengali sentence pairs
* 200 Hindi sentence pairs

This ensures manageable and balanced comparisons.

---

## Step 5 — Tokenization Analysis

For each sentence pair:

* Native-script token count is computed
* Romanized token count is computed

This is repeated for:

* GPT tokenizer
* MuRIL tokenizer
* mBERT tokenizer

---

# Metrics

## 1. Script Sensitivity Ratio (SSR)

Measures how much tokenization changes between native and romanized forms.

General interpretation:

* Higher SSR → greater sensitivity to script changes
* Lower SSR → more stable tokenization across scripts

---

## 2. Native Script Load (NSL)

Compares tokenization efficiency across models.

Example:

```text
NSL (GPT vs MuRIL)
```

Interpretation:

* Value > 1 → GPT produces more tokens than MuRIL
* Value < 1 → GPT produces fewer tokens

---

# Visualizations

The notebook generates:

## Heatmaps

For both Bengali and Hindi:

* Native script NSL matrix
* Romanized script NSL matrix
* Difference heatmaps

These visualize comparative tokenization efficiency across models.

---

## Comparative Bar Charts

Displays:

* Bengali SSR values
* Hindi SSR values

across:

* GPT
* MuRIL
* mBERT

---

# Project Structure

```text
SALA.ipynb
│
├── Dataset loading
├── Data filtering and cleaning
├── Bengali tokenization analysis
├── Hindi tokenization analysis
├── SSR computation
├── NSL computation
├── Heatmap visualizations
└── Cross-language comparison plots
```

---

# Installation

## Clone Repository

```bash
git clone <repository-url>
cd <repository-folder>
```

---

## Install Dependencies

```bash
pip install numpy matplotlib transformers datasets tiktoken
```

---

# Running the Notebook

Launch Jupyter Notebook:

```bash
jupyter notebook SALA.ipynb
```

or use:

```bash
jupyter lab
```

Run all cells sequentially.

---

# Dependencies

The notebook uses:

* Python 3.x
* NumPy
* Matplotlib
* Hugging Face Transformers
* Hugging Face Datasets
* tiktoken

---

# Expected Outputs

The notebook produces:

* Token count comparisons
* Mean SSR values
* NSL matrices
* Heatmaps
* Cross-language comparison plots

These outputs help evaluate how multilingual tokenizers behave with Indic scripts and romanization.

---

# Potential Research Extensions

Possible future directions include:

* Expanding to additional Indic languages
* Comparing sentencepiece vs BPE tokenizers
* Evaluating downstream model performance
* Measuring tokenization effects on generation cost
* Studying code-switching and mixed-script input
* Investigating tokenization bias in LLMs

---

# Academic Relevance

This project contributes to ongoing research in:

* Indic NLP
* Multilingual representation learning
* Tokenization studies
* Script processing
* Low-resource language technologies
* Computational sociolinguistics

---

# Citation

If you use this notebook in academic work, please cite:

```text
AI4Bharat Bhasha-Abhijnaanam Dataset
MuRIL: Multilingual Representations for Indian Languages
mBERT: Multilingual BERT
```

---

# Author

Prepared for computational linguistics and multilingual NLP research.

---

# License

Add an appropriate license if distributing publicly.
