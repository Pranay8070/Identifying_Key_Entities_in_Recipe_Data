# 🍳 Identifying Key Entities in Recipe Data

## 1. Objective

This project focuses on building a system to recognize key components in cooking recipes using a Named Entity Recognition (NER) approach. The system identifies the following entities:

- **Ingredients**
- **Quantities**
- **Measurement units**

By extracting these entities from unstructured recipe text, the model converts them into a structured format. This enables applications such as:

- Nutritional tracking  
- Automated grocery lists  
- Interactive cooking apps  

---

## 2. Methodology

### 🔹 Data Preparation

- The recipe dataset is pre-tagged using the **IOB format** (Inside, Outside, Beginning), commonly used in NER tasks.
- Each word in the text is labeled as B-<entity>, I-<entity>, or O.

### 🔹 Feature Engineering

Each token is enriched with features to improve entity recognition:

- Lowercase form of the word  
- Part-of-speech (POS) tags  
- Prefixes and suffixes  
- Whether the token is capitalized or numeric  
- Position in sentence and surrounding context  

### 🔹 Model Development

- We use **Conditional Random Fields (CRF)** implemented via `sklearn-crfsuite`, ideal for structured sequence prediction.
- The model is evaluated using standard classification metrics: **precision**, **recall**, and **F1-score**.

---

## 3. Visualizations and Insights

### 📊 Entity Frequency

- Common ingredients: `powder`, `salt`, `seeds`
- Common units: `teaspoon`, `cup`, `tablespoon`

### 🔍 Observations

- **Ingredients** are the most frequently tagged entities.
- **Units** and **quantities** follow consistent language patterns, aiding recognition.

### 📈 Model Performance

| Entity      | Precision | Recall | F1-score | Support |
|-------------|-----------|--------|----------|---------|
| Ingredient  | 0.99      | 0.99   | 0.99     | 1611    |
| Quantity    | 0.99      | 0.97   | 0.98     | 294     |
| Unit        | 0.96      | 0.95   | 0.95     | 244     |
| **Overall Accuracy** |        |        | **0.98** | **2149** |

### 💡 Key Insights

- Ingredient detection is highly accurate due to well-designed features.
- Slightly lower recall for quantities and units due to variations like _“a pinch”_ or _“half”_.
- Macro and weighted F1-scores are consistently high (~0.97–0.98), indicating model balance.

---

## 4. Assumptions Made

- The dataset is accurately labeled in IOB format.
- Each sentence or line in the recipe is treated independently.
- The model does **not** use pre-trained embeddings or language models.
- All features are **manually engineered**.

---

## 5. Conclusion

The CRF-based NER model achieves strong results with **98% accuracy** in identifying structured elements from recipe data. This highlights the potential of traditional, feature-based models for tasks involving patterned and domain-specific text.
