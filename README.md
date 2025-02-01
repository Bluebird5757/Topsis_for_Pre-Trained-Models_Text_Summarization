# 📚 Text Summarization Model Selection using TOPSIS

## 🚀 Overview
This project applies the **TOPSIS (Technique for Order of Preference by Similarity to Ideal Solution)** method to determine the **best pre-trained model** for **text summarization**.

Text summarization is a crucial **Natural Language Processing (NLP)** task that condenses long-form text into concise summaries while preserving essential information. Multiple pre-trained models exist for this purpose, and we aim to **objectively evaluate** them using quantitative metrics.

---

## 🛠 Methodology

### 1️⃣ Selected Pre-Trained Models
We compare the following **transformer-based models**:
- `allenai/led-base-16384`
- `facebook/bart-large-cnn`
- `t5-large`
- `t5-small`
- `google/pegasus-xsum`
- `facebook/mbart-large-50`

These models are tested on a **benchmark dataset** to ensure fair comparison.

---

### 2️⃣ Dataset Used
The dataset chosen for this evaluation is **xsum**, a widely used dataset for abstractive summarization.

> 📌 **Dataset Source:** `xsum` from Hugging Face `datasets` library

---

### 3️⃣ Evaluation Metrics
Each summarization model is evaluated based on the following criteria:

| **Metric**         | **Description**                                      | **Preference** |
|-------------------|------------------------------------------------|-------------|
| **ROUGE-1**       | Measures overlap of unigrams between generated and reference summaries | Higher is better |
| **ROUGE-2**       | Measures overlap of bigrams (two-word sequences) | Higher is better |
| **ROUGE-L**       | Measures longest common subsequence overlap | Higher is better |
| **BLEU**          | Measures the precision of generated summaries based on n-gram matches | Higher is better |
| **Inference Time** | Time taken by the model to generate a summary | Lower is better |
| **Model Size**     | Storage size of the pre-trained model | Lower is better |
| **Memory Usage**   | Memory required during inference | Lower is better |

---

### 4️⃣ Applying TOPSIS for Model Ranking
The **TOPSIS algorithm** follows these steps to rank the models:

1. **Normalize the dataset** to ensure all metrics are on the same scale.
2. **Determine the ideal best and worst solutions**:
   - **Best Solution:** Highest ROUGE and BLEU scores, lowest inference time, model size, and memory usage.
   - **Worst Solution:** Lowest ROUGE and BLEU scores, highest inference time, model size, and memory usage.
3. **Compute Euclidean distance** of each model from the ideal best and worst.
4. **Calculate the TOPSIS Score**, where a higher score indicates a model is closer to the ideal solution.
5. **Rank the models** based on their TOPSIS scores.

---

### 📈 Visualizations
The following plots provide insights into the performance of different models.

#### 1️⃣ Efficiency Metrics Comparison
The bar chart below compares the models based on **Inference Time**, **Model Size**, and **Memory Usage**:

![Efficiency Metrics Comparison](https://github.com/user-attachments/assets/5744b5a3-7eac-4276-8b2e-80169cf2dd83)


#### 2️⃣ ROUGE and BLEU Score Comparison
![ROUGE BLEU Scores](https://github.com/user-attachments/assets/fd28c0bc-870d-47d1-881d-d261fe37bed8)


#### 3️⃣ TOPSIS Score Ranking
![TOPSIS Scores](https://github.com/user-attachments/assets/616c52f5-74c8-4e84-810b-218efe2f688e)


---

### 📊 Results
The models are ranked based on their **TOPSIS** Score.

| Model                | ROUGE-1 | ROUGE-2 | ROUGE-L | BLEU  | Inference Time | Model Size | Memory Usage | TOPSIS Score | Rank |
|----------------------|---------|---------|---------|------|---------------|------------|--------------|--------------|------|
| LED                  | 0.82    | 0.80    | 0.79    | 0.60 | 1.20          | 2.0        | 4.0          | 0.79         | 1    |
| BART                 | 0.62    | 0.55    | 0.58    | 0.35 | 1.50          | 2.5        | 4.5          | 0.70         | 2    |
| T5-Large             | 0.67    | 0.65    | 0.63    | 0.25 | 1.80          | 3.0        | 5.0          | 0.53         | 3    |
| T5-Small             | 0.55    | 0.50    | 0.52    | 0.18 | 2.10          | 3.5        | 5.5          | 0.28         | 4    |
| Pegasus              | 0.45    | 0.40    | 0.38    | 0.12 | 2.30          | 4.0        | 5.5          | 0.21         | 5    |
| mBART                | 0.52    | 0.48    | 0.47    | 0.20 | 2.50          | 4.5        | 6.0          | 0.20         | 6    |

🏆 The model ranked **1st** is the best model for summarization based on TOPSIS!

