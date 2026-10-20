# Network Intrusion Detection Using Machine Learning

### Cybersecurity Analytics | Python · Scikit-learn · Random Forest

## Project Overview

This project explores the use of machine learning to distinguish malicious network traffic from normal network activity.

Using the **UNSW-NB15 cybersecurity dataset**, the analysis examines network connection characteristics and builds a supervised classification pipeline to identify potentially malicious traffic.

The project covers data exploration, preprocessing, model training, and evaluation.

## Dataset

**Source:** [UNSW-NB15 Dataset — Kaggle](https://www.kaggle.com/datasets/dhoogla/unswnb15)

The dataset contains network traffic records representing normal activity and simulated cyberattacks.

| Dataset | Records | Features and label columns |
|---|---:|---:|
| Training | 175,341 | 36 |
| Testing | 82,332 | 36 |
| Total | 257,673 | 36 |

The dataset includes connection duration, network protocol, service, connection state, packet counts, transferred bytes, and other traffic-related characteristics.

The target variable, `label`, indicates whether a record represents normal or malicious traffic.

## Tools & Technologies

- **Python** — Data processing and machine learning
- **Pandas & NumPy** — Data exploration and manipulation
- **Scikit-learn** — Preprocessing, classification, and evaluation
- **Matplotlib & Seaborn** — Data visualization
- **KaggleHub** — Dataset retrieval
- **Jupyter Notebook** — Development environment

## Methodology

### 1. Data Collection & Exploration

Retrieved the UNSW-NB15 dataset using KaggleHub and loaded the provided training and testing files.

Examined the dataset structure, feature types, missing values, and class distribution.

The training dataset contains:

- **119,341 malicious traffic records**
- **56,000 normal traffic records**

This represents an imbalanced classification problem, with approximately 68% of the training observations labeled as malicious.

### 2. Data Preprocessing

Prepared numerical and categorical features using a Scikit-learn preprocessing pipeline.

- Applied median imputation to numerical features.
- Applied most-frequent imputation to categorical features.
- Encoded categorical variables using OneHotEncoder.
- Removed the target label and identified potential nonpredictive or leakage-prone columns.
- Preserved the provided training and testing partitions.

Using a pipeline ensures that preprocessing transformations are fitted on training data and applied consistently to test data.

### 3. Machine Learning Model

Implemented a **Random Forest Classifier** to identify malicious network traffic.

The model learns patterns from network traffic characteristics and produces predictions for the binary classification task.

A Scikit-learn Pipeline combines preprocessing and classification into a reproducible workflow.

### 4. Model Evaluation

The notebook uses classification evaluation tools including:

- **Precision:** How many predicted attacks were actually attacks.
- **Recall:** How many actual attacks were detected.
- **F1-score:** A balance between precision and recall.
- **Confusion matrix:** Correct and incorrect classifications for each class.
- **ROC-AUC:** How well the model separates malicious and normal traffic across classification thresholds.

These metrics are particularly relevant in cybersecurity, where both missed attacks and false alarms have operational consequences.

## Key Analytical Considerations

### Class Imbalance

The training dataset contains substantially more malicious than normal observations.

Therefore, accuracy alone may not provide a complete picture of model performance.

Precision, recall, F1-score, and ROC-AUC provide additional perspectives on classification quality.

### False Positives and False Negatives

A false positive occurs when normal traffic is incorrectly flagged as malicious.

A false negative occurs when malicious traffic is classified as normal.

In real cybersecurity environments, false negatives may leave threats undetected, while excessive false positives can overwhelm security analysts.

### Reproducible Preprocessing

Using Scikit-learn pipelines reduces inconsistencies between training and testing transformations and helps prevent data leakage.

## Limitations

- UNSW-NB15 contains benchmark traffic, which may not fully represent modern production networks.
- Performance on the provided test dataset does not guarantee performance in real-world environments.
- Class distributions and attack patterns may differ from those encountered in operational systems.
- Model evaluation should consider the trade-off between missed attacks and false alarms.

## Future Improvements

Potential extensions include comparing multiple classification algorithms, tuning decision thresholds, investigating feature importance, and evaluating performance across different attack categories.

## Dataset Source

[UNSW-NB15 — Kaggle](https://www.kaggle.com/datasets/dhoogla/unswnb15)
