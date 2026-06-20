# Network Anomaly Detection with NSL-KDD

A machine learning project for detecting network anomalies and classifying intrusion types using the NSL-KDD dataset.

The project focuses on multi-class classification of network traffic into normal and attack categories using classical machine learning models such as Random Forest and XGBoost.

## Overview

This project uses the NSL-KDD dataset, a benchmark dataset commonly used for evaluating intrusion detection systems.

The goal is to classify network traffic into multiple categories:

- Normal Traffic
- DoS Attack
- Probe Attack
- Access Attack
- Privilege Escalation Attack

The project compares machine learning models and evaluates their performance using classification metrics such as precision, recall, F1-score, and accuracy.

## Features

- Network anomaly detection
- Multi-class intrusion classification
- NSL-KDD dataset preprocessing
- Train/validation/test split
- Random Forest model training
- XGBoost model training
- Pipeline-based workflow
- GridSearchCV hyperparameter tuning
- Classification report evaluation
- Analysis of class imbalance
- Discussion of rare-class performance

## Technologies Used

- Python
- Pandas
- NumPy
- scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Jupyter Notebook

## Dataset

This project uses the NSL-KDD dataset.

NSL-KDD is an improved version of the original KDD Cup 1999 dataset and is widely used for intrusion detection and network anomaly detection research.

The dataset contains network connection records with features describing traffic behavior, protocol information, service information, and attack labels.

## Classification Categories

The project groups traffic into the following main classes:

```text
Normal Traffic
DoS Attack
Probe Attack
Access Attack
Privilege Escalation
```

### Normal Traffic

Legitimate network traffic without malicious activity.

### DoS Attack

Denial-of-Service attacks that attempt to make a system or network resource unavailable.

### Probe Attack

Scanning and probing activity used to discover hosts, services, or vulnerabilities.

### Access Attack

Unauthorized access attempts against a system or service.

### Privilege Escalation

Attempts to gain higher-level permissions after initial access.

## Machine Learning Workflow

```text
Raw NSL-KDD data
        ↓
Data preprocessing
        ↓
Feature engineering / encoding
        ↓
Train-validation-test split
        ↓
Model training
        ↓
GridSearchCV hyperparameter tuning
        ↓
Model evaluation
        ↓
Classification report
```

## Models Used

### Random Forest

Random Forest is an ensemble learning model based on multiple decision trees. It is useful for tabular classification problems and can handle non-linear feature relationships.

### XGBoost

XGBoost is a gradient boosting algorithm optimized for performance and accuracy. In this project, XGBoost achieved the best overall classification performance.

## Results

The best performing model was **XGBoost**.

The project achieved very high accuracy overall, with near-perfect performance on most major classes.

Example classification results:

```text
Class                  Precision    Recall    F1-score

Normal Traffic            1.00      1.00        1.00
DoS Attack                1.00      1.00        1.00
Probe Attack              0.99      1.00        0.99
Privilege Escalation      0.82      0.61        0.70
Access Attack             0.98      0.93        0.95
```

## Result Interpretation

The model performs extremely well on common traffic and major attack classes such as Normal, DoS, Probe, and Access attacks.

The weakest performance is on the **Privilege Escalation** class. This is expected because privilege escalation examples are rare in the dataset, making the model harder to train for that class.

This shows an important machine learning challenge in cybersecurity: class imbalance.

## Class Imbalance

Some attack categories have far fewer samples than others.

For example, privilege escalation attacks are rare compared to normal traffic or DoS attacks. As a result, the model has fewer examples to learn from, which can reduce recall on rare classes.

Possible improvements include:

- SMOTE oversampling
- class weights
- collecting more rare-class samples
- additional feature engineering
- threshold tuning
- model calibration

## Project Structure

```text
network-anomaly-detection-nsl-kdd/
├── notebook.ipynb
├── requirements.txt
└── README.md
```

Adjust file names based on the actual notebook name in the repository.

## Installation

Clone the repository:

```bash
git clone https://github.com/chrispsk/network-anomaly-detection-nsl-kdd.git
cd network-anomaly-detection-nsl-kdd
```

Create and activate a virtual environment:

```bash
python -m venv venv
```

On Windows:

```bash
venv\Scripts\activate
```

On macOS/Linux:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

If there is no `requirements.txt`, install the main dependencies manually:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
```

## Usage

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook and run the cells from top to bottom.

## Recommended `requirements.txt`

```text
pandas
numpy
scikit-learn
xgboost
matplotlib
seaborn
jupyter
```

## Example Use Case

This project simulates a machine learning workflow for an intrusion detection system.

Given network traffic features, the trained model predicts whether the traffic is normal or belongs to a known attack category.

Example prediction classes:

```text
Normal
DoS
Probe
Access
Privilege
```

## Notes

It demonstrates:

- intrusion detection concepts;
- supervised anomaly detection;
- multi-class classification;
- model comparison;
- hyperparameter tuning;
- evaluation of imbalanced security datasets.

## Possible Improvements

- Add SMOTE for rare attack classes
- Add class weighting
- Add confusion matrix visualization
- Add feature importance analysis
- Add model export with `joblib`
- Add ROC-AUC or PR-AUC metrics
