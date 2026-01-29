# Understanding Political Bias in News Text Classification

This repository contains the experimental notebooks and analyses developed for the academic project **“Understanding Political Bias in News Text Classification”**.  
The work investigates how text classification models learn and exploit different types of signals when performing political bias detection in news text.

Rather than redefining political ideologies, this project treats political bias labels as given and focuses on **model behavior, shortcut learning, and interpretability** in politically sensitive NLP tasks.

---

## Project Overview

Automated political bias detection has become increasingly relevant in applications such as media analysis and content moderation. However, strong predictive performance alone does not guarantee meaningful ideological understanding.

This project adopts a **data-centric and interpretability-driven perspective**, aiming to answer the following questions:

- Do models rely on **semantic political content**, or on **structural and source-related shortcuts**?
- How does model behavior change across datasets with different characteristics?
- Can interpretability and masking strategies reveal hidden dependencies beyond standard performance metrics?

To address these questions, the project compares models, datasets, and signal families under controlled experimental conditions.

---

## Datasets

Two publicly available datasets with complementary characteristics are used.

### Dataset 1: Article-Level Political Bias
- Full news articles annotated with political bias.
- Original five-class labels consolidated into three classes: **left**, **center**, **right**.
- Each news outlet is consistently associated with a single political bias label.
- Rich in **structural and source-related cues**, such as formatting artifacts and outlet identifiers.

This dataset supports the analysis of **shortcut learning** based on publication-specific patterns rather than ideological content.

### Dataset 2: Media Bias Including Characteristics (MBIC)
- Short sentence-level statements annotated for political bias.
- Includes word-level annotations of biased expressions.
- No source information and minimal contextual structure.
- Focused exclusively on instances labeled as biased.

This dataset is designed to isolate **semantic bias cues** and supports controlled masking experiments.

---

## Models

Two fundamentally different classification approaches are evaluated.

### TF-IDF + Logistic Regression
- Linear classifier using TF-IDF representations (unigrams and bigrams).
- Class-balanced training to mitigate class imbalance.
- Chosen for transparency and interpretability.

This model enables detailed analysis of lexical, structural, and source-related feature importance.

### BERT-Based Classifier
- Pre-trained BERT fine-tuned for three-class political bias classification.
- Captures contextual and semantic information beyond surface-level features.
- Model selection based on macro F1-score.

The comparison highlights differences in robustness, generalization, and reliance on shortcuts.

---

## Experimental Design

All experiments follow a consistent evaluation protocol:

- Fixed 80/20 train–test split.
- Evaluation using precision, recall, and F1-score per class.
- **Macro F1-score** used as the primary comparison metric due to class imbalance.

Beyond standard evaluation, the project emphasizes **probing model behavior** through interpretability and masking strategies.

---

## Interpretability and Masking

To go beyond aggregate metrics, multiple analysis techniques are combined.

### Interpretability
- **LIME** for local explanations of TF-IDF models.
- **Transformers Interpret** for token-level attribution in BERT.
- Global feature importance analysis for linear models.

Explanations are analyzed across:
- Correct and incorrect predictions
- High- and low-confidence predictions
- Different political bias classes

### Masking Experiments
- Structural and source-related expressions masked in article-level data.
- Annotated biased words masked in sentence-level data.
- Additional experiments train models directly on masked text.
- A final probing experiment trains models using **only biased words**.

These experiments test prediction stability and reveal which signal families models depend on most.

---

## Key Findings

The main findings can be summarized as follows:

- High performance on article-level data often relies on **structural and source-related shortcuts**.
- Masking such cues significantly affects predictions, especially for right-leaning and centrist content.
- Sentence-level semantic cues alone are **insufficient for robust political bias classification**.
- BERT shows increased robustness compared to TF-IDF models, but remains fragile in ambiguous cases.
- The **center** class consistently emerges as the most unstable and difficult to model.

Overall, predictive success does not necessarily imply meaningful ideological understanding.

---

## Societal and Ethical Considerations

Political bias classification is a socially sensitive task with real-world implications.  
This project highlights risks such as:

- Reinforcement of media stereotypes
- Overreliance on dataset-specific artifacts
- Misclassification of nuanced or centrist positions

The findings emphasize the importance of **interpretability, transparency, and careful dataset design** when deploying AI systems in political and societal contexts.
