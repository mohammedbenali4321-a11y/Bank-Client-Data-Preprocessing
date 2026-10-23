# 📊 Bank Client Data Preprocessing & Feature Engineering

Welcome to the **Bank Client Data Preprocessing** repository! This project focuses on preparing a complex banking dataset containing customer demographics, financial records, and categorical behavior indicators for downstream Machine Learning models.

---

## 📌 Table of Contents
- [Overview](#overview)
- [Dataset Characteristics](#dataset-characteristics)
- [Key Data Preprocessing Steps](#key-data-preprocessing-steps)
- [Summary of Transformations](#summary-of-transformations)
- [Tech Stack](#tech-stack)
- [Repository Structure](#repository-structure)
- [Connect & Follow](#connect--follow)

---

## 🔎 Overview

In financial and banking analytics, raw data is often dirty, incomplete, and contains a mix of non-comparable scales and categorical data types. 

This project demonstrates an end-to-end data preprocessing pipeline using **Python**, **Pandas**, and **Scikit-Learn**, performing essential steps including missing value imputation, numerical scaling (Min-Max Normalization & Standard Standardization), and categorical encodings (One-Hot & Ordinal).

---

## 📋 Dataset Characteristics

The original dataset (`jeu_donnees_clients_banque_100_lignes.xlsx`) consists of **100 customer records** across **10 features**:

| Feature Name | Description | Group Type |
| :--- | :--- | :--- |
| `ID_Client` | Unique identifier per client | Identifier |
| `Age` | Client's age (years) | Numerical |
| `Revenu_annuel_DH` | Annual income in Dirhams | Numerical |
| `Solde_DH` | Account balance in Dirhams | Numerical |
| `Anciennete_mois` | Account tenure (months) | Numerical |
| `Ville` | Moroccan city of residence | Categorical (Nominal) |
| `Profession` | Employment category | Categorical (Nominal) |
| `Niveau_etudes` | Highest education level completed | Categorical (Ordinal) |
| `Satisfaction` | Client satisfaction index | Categorical (Ordinal) |
| `Statut` | Client type (`Client` vs `Prospect`) | Categorical (Target/Status) |

---

## 🛠️ Key Data Preprocessing Steps

### 1. Data Cleaning & Missing Value Handling
- **Numerical Features** (`Revenu_annuel_DH`, `Solde_DH`, `Anciennete_mois`): Imputed using the **median** value to maintain robustness against outliers and skewed distributions.
- **Categorical Features** (`Ville`, `Profession`, `Niveau_etudes`, `Satisfaction`): Imputed using the **mode** (most frequent class).

### 2. Feature Scaling & Feature Transformation
- **Min-Max Scaling (`MinMaxScaler`)**: Transforms numerical scales into the bounded range $[0, 1]$, removing original measurement units while handling negative values (e.g., bank overdraft balances).
- **Standardization (`StandardScaler`)**: Standardizes features to a mean of $0$ ($\mu = 0$) and standard deviation of $1$ ($\sigma = 1$). Ideal for distance-based algorithms (KNN, SVM, K-Means) and gradient descent optimization.

### 3. Categorical Encodings
- **One-Hot Encoding (`get_dummies` / `OneHotEncoder`)**: Applied to nominal variables (`Ville`, `Profession`) with no inherent order. Generates $15$ binary columns ($8$ cities + $7$ professions).
- **Ordinal Encoding (`OrdinalEncoder`)**: Preserves the explicit logical hierarchy:
  - **`Niveau_etudes`**: $\text{Bac} < \text{Licence} < \text{Master} < \text{Doctorat}$
  - **`Satisfaction`**: $\text{Faible} < \text{Moyenne} < \text{Élevée} < \text{Très élevée}$

---

## 📑 Summary of Transformations

| Feature Name | Type | Processing Technique Applied |
| :--- | :--- | :--- |
| `ID_Client` | Identifier | Dropped from modeling (non-predictive) |
| `Age`, `Revenu_annuel_DH`, `Solde_DH`, `Anciennete_mois` | Numerical | Median Imputation + `MinMaxScaler` / `StandardScaler` |
| `Ville`, `Profession` | Nominal | Mode Imputation + `OneHotEncoder` |
| `Niveau_etudes`, `Satisfaction` | Ordinal | Mode Imputation + `OrdinalEncoder` |

---

## 💻 Tech Stack

- **Python** `3.x`
- **Pandas** for data manipulation and analysis
- **NumPy** for numerical calculations
- **Scikit-Learn** for preprocessing pipelines (`MinMaxScaler`, `StandardScaler`, `OneHotEncoder`, `OrdinalEncoder`)

---

## 🔗 Connect & Follow

Feel free to reach out, connect, or explore my other projects across platforms:

- **GitHub Profile**: [Mohamed BEN ALI](https://github.com/mohammedbenali4321-a11y)
- **LinkedIn**: [Mohamed BEN ALI](https://www.linkedin.com/in/mohamed-ben-ali-m)
- **Kaggle**: [Mohamed BEN ALI](https://www.kaggle.com/mohamedbenali4321)
- **Roadmap.sh**: [Mohamed's Developer Roadmap](https://roadmap.sh/u/benalimohamed)

---
*Created as part of the Data Analyst Preprocessing Practical Work.*