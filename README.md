<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0f0c29,50:302b63,100:24243e&height=200&section=header&text=CODSOFT%20DATA%20SCIENCE&fontSize=42&fontColor=ffffff&fontAlignY=38&desc=Internship%20Projects%20%7C%20Machine%20Learning%20in%20Python&descAlignY=58&descSize=16&animation=fadeIn"/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![Status](https://img.shields.io/badge/Status-Completed-22c55e?style=for-the-badge&logo=checkmarx&logoColor=white)]()
[![Internship](https://img.shields.io/badge/CODSOFT-Internship-ff6b6b?style=for-the-badge&logoColor=white)]()

<br/>

> **5 end-to-end Machine Learning projects** — classification, regression, fraud detection, and forecasting — built with real-world datasets and production-grade Python workflows.

<br/>

![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&size=18&pause=1000&color=38BDF8&center=true&vCenter=true&width=600&lines=Exploring+Data+Science+with+CODSOFT;Building+Real-World+ML+Models;From+Raw+Data+to+Intelligent+Predictions)

</div>

---

## 🧭 Table of Contents

- [📌 About](#-about)
- [🚀 Projects Overview](#-projects-overview)
- [🚢 Task 1 — Titanic Survival Prediction](#-task-1--titanic-survival-prediction)
- [🎬 Task 2 — Movie Rating Prediction](#-task-2--movie-rating-prediction)
- [🌸 Task 3 — Iris Flower Classification](#-task-3--iris-flower-classification)
- [📈 Task 4 — Sales Prediction](#-task-4--sales-prediction)
- [🛡️ Task 5 — Credit Card Fraud Detection](#️-task-5--credit-card-fraud-detection)
- [🔬 ML Pipeline](#-ml-pipeline)
- [🛠️ Tech Stack](#️-tech-stack)
- [⚙️ Setup & Installation](#️-setup--installation)
- [📁 Repository Structure](#-repository-structure)
- [📬 Connect](#-connect)

---

## 📌 About

This repository contains all five Data Science projects completed as part of the **CODSOFT Data Science Internship**. Each project covers a unique problem domain and demonstrates core ML competencies including exploratory data analysis, feature engineering, model training, hyperparameter tuning, and rigorous evaluation.

| 🔢 Stat | 📊 Value |
|--------|---------|
| Total Projects | 5 |
| Language | Python 3.10+ |
| Notebooks | Jupyter (.ipynb) |
| Algorithms Used | 10+ |
| Domains Covered | Classification · Regression · Anomaly Detection · Forecasting |

---

## 🚀 Projects Overview
┌──────────────────────────────────────────────────────────────────┐
│  #   │  Project                        │  Type          │  Algo  │
├──────────────────────────────────────────────────────────────────┤
│  01  │  Titanic Survival Prediction    │  Classification│  RF    │
│  02  │  Movie Rating Prediction        │  Regression    │  XGB   │
│  03  │  Iris Flower Classification     │  Multi-class   │  SVM   │
│  04  │  Sales Prediction               │  Regression    │  LR    │
│  05  │  Credit Card Fraud Detection    │  Classification│  RF+LR │
└──────────────────────────────────────────────────────────────────┘

---

## 🚢 Task 1 — Titanic Survival Prediction

<img src="https://img.shields.io/badge/Type-Binary%20Classification-38bdf8?style=flat-square"/> <img src="https://img.shields.io/badge/Dataset-Kaggle%20Titanic-orange?style=flat-square&logo=kaggle"/> <img src="https://img.shields.io/badge/Algorithm-Random%20Forest-22c55e?style=flat-square"/>

> *"Predict who survives the unsinkable ship."*

The Titanic dataset is the cornerstone of classification learning. Using passenger information — age, sex, ticket class, cabin, and fare — we engineer meaningful features and train an ensemble model to predict survival.

**📂 Key Steps**
- ✅ Handle missing values in `Age`, `Cabin`, `Embarked`
- ✅ Encode categorical features (`Sex`, `Embarked`)
- ✅ Engineer `FamilySize`, `IsAlone`, `Title` from name
- ✅ Train Random Forest with cross-validation
- ✅ Visualize feature importances and confusion matrix

**📊 Results**

| Metric | Score |
|--------|-------|
| Accuracy | ~83% |
| Precision | ~81% |
| Recall | ~79% |
| F1-Score | ~80% |

---

## 🎬 Task 2 — Movie Rating Prediction

<img src="https://img.shields.io/badge/Type-Regression-818cf8?style=flat-square"/> <img src="https://img.shields.io/badge/Dataset-IMDB%20Movies-yellow?style=flat-square"/> <img src="https://img.shields.io/badge/Algorithm-XGBoost-f97316?style=flat-square"/>

> *"Decode what makes a movie a masterpiece — or a flop."*

We analyze historical movie data and build a regression model that estimates the rating a movie will receive based on metadata: genre, director, cast, release year, and runtime.

**📂 Key Steps**
- ✅ Parse and clean multi-value `Genre` and `Cast` columns
- ✅ Apply Target Encoding for high-cardinality director/actor fields
- ✅ Handle skewed distributions with log-transformations
- ✅ Train XGBoost Regressor with GridSearchCV
- ✅ Plot predicted vs actual ratings

**📊 Results**

| Metric | Score |
|--------|-------|
| MAE | ~0.48 |
| RMSE | ~0.71 |
| R² Score | ~0.79 |

---

## 🌸 Task 3 — Iris Flower Classification

<img src="https://img.shields.io/badge/Type-Multi--class%20Classification-34d399?style=flat-square"/> <img src="https://img.shields.io/badge/Dataset-UCI%20Iris-blueviolet?style=flat-square"/> <img src="https://img.shields.io/badge/Algorithm-SVM%20%7C%20KNN%20%7C%20LR-ec4899?style=flat-square"/>

> *"Three species. Four features. Perfect separability."*

The classic entry point for ML classification. We train and compare multiple models on sepal/petal measurements and visualize decision boundaries across species.

**📂 Key Steps**
- ✅ Visualize pairplots and correlations across three species
- ✅ Standardize features with `StandardScaler`
- ✅ Train and compare SVM, KNN, Logistic Regression, Decision Tree
- ✅ Plot decision boundary for best model
- ✅ Generate classification report per species

**📊 Results**

| Model | Accuracy |
|-------|----------|
| SVM (RBF) | **98.7%** |
| KNN (k=5) | 97.3% |
| Logistic Regression | 96.0% |
| Decision Tree | 95.3% |

---

## 📈 Task 4 — Sales Prediction

<img src="https://img.shields.io/badge/Type-Regression%20%7C%20Forecasting-fb923c?style=flat-square"/> <img src="https://img.shields.io/badge/Dataset-Advertising%20CSV-lightgrey?style=flat-square"/> <img src="https://img.shields.io/badge/Algorithm-Linear%20Regression-38bdf8?style=flat-square"/>

> *"Tell me your ad budget — I'll tell you your revenue."*

Using advertising expenditure across TV, Radio, and Newspaper channels, we build a regression model to forecast sales and help businesses optimize marketing budget allocation.

**📂 Key Steps**
- ✅ Exploratory analysis of spend-to-sales correlation
- ✅ Check for multicollinearity with VIF scores
- ✅ Train Linear, Ridge, and Lasso regression models
- ✅ Residual analysis and normality tests
- ✅ Feature importance via regression coefficients

**📊 Results**

| Metric | Score |
|--------|-------|
| R² Score | ~0.91 |
| MAE | ~1.21 |
| RMSE | ~1.69 |

---

## 🛡️ Task 5 — Credit Card Fraud Detection

<img src="https://img.shields.io/badge/Type-Anomaly%20Detection-f87171?style=flat-square"/> <img src="https://img.shields.io/badge/Dataset-Kaggle%20Credit%20Card-blue?style=flat-square&logo=kaggle"/> <img src="https://img.shields.io/badge/Technique-SMOTE%20%2B%20Random%20Forest-22c55e?style=flat-square"/>

> *"Find the needle in a 284,807-transaction haystack."*

The most challenging task: detecting fraudulent transactions in a massively imbalanced dataset (fraud < 0.2% of data). We apply SMOTE for oversampling and evaluate with precision-recall metrics to protect real users.

**📂 Key Steps**
- ✅ Analyze severe class imbalance (fraud: ~0.17%)
- ✅ Normalize `Amount` and `Time` features
- ✅ Apply **SMOTE** to oversample minority class
- ✅ Train Random Forest and Logistic Regression
- ✅ Evaluate with Precision-Recall curve, ROC-AUC, F1-Score

**📊 Results**

| Metric | Score |
|--------|-------|
| Precision | ~94% |
| Recall | ~92% |
| F1-Score | ~93% |
| ROC-AUC | ~0.97 |

---

## 🔬 ML Pipeline

Every project follows this consistent end-to-end workflow:
📥 Data Ingestion
↓
🔍 Exploratory Data Analysis (EDA)
↓
🧹 Data Preprocessing
├── Handle missing values
├── Encode categorical variables
└── Scale / normalize features
↓
⚙️ Feature Engineering
├── Create new informative features
└── Select relevant features
↓
🤖 Model Training
├── Train-test split (80/20)
├── Cross-validation (k=5)
└── Hyperparameter tuning (GridSearchCV)
↓
📊 Model Evaluation
├── Classification: Accuracy, Precision, Recall, F1, ROC-AUC
└── Regression: MAE, RMSE, R²
↓
📈 Visualization & Insights

---

## 🛠️ Tech Stack

<div align="center">

| Category | Libraries |
|----------|-----------|
| **Language** | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) |
| **Data** | ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) |
| **ML** | ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white) ![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=flat-square) |
| **Imbalanced** | ![imbalanced-learn](https://img.shields.io/badge/imbalanced--learn-22c55e?style=flat-square) |
| **Visualization** | ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=flat-square) ![Seaborn](https://img.shields.io/badge/Seaborn-4c9be8?style=flat-square) |
| **Environment** | ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white) |

</div>

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/codsoft-ds-internship.git
cd codsoft-ds-internship
```

**2. Create a virtual environment**
```bash
python -m venv .venv
source .venv/bin/activate        # macOS/Linux
.venv\Scripts\activate           # Windows
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Launch Jupyter Notebook**
```bash
jupyter notebook
```

**`requirements.txt`**
numpy
pandas
matplotlib
seaborn
scikit-learn
xgboost
imbalanced-learn
jupyter
scipy

---

## 📁 Repository Structure
codsoft-ds-internship/
│
├── 📂 Task1_Titanic/
│   ├── titanic.ipynb
│   ├── data/
│   └── README.md
│
├── 📂 Task2_MovieRating/
│   ├── movie_rating.ipynb
│   ├── data/
│   └── README.md
│
├── 📂 Task3_Iris/
│   ├── iris_classification.ipynb
│   ├── data/
│   └── README.md
│
├── 📂 Task4_SalesPrediction/
│   ├── sales_prediction.ipynb
│   ├── data/
│   └── README.md
│
├── 📂 Task5_FraudDetection/
│   ├── fraud_detection.ipynb
│   ├── data/
│   └── README.md
│
├── requirements.txt
└── README.md

---

## 📬 Connect

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/yourprofile)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/yourusername)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:your@email.com)

<br/>

*If this helped you, please give it a ⭐ — it means a lot!*

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:24243e,50:302b63,100:0f0c29&height=120&section=footer&animation=fadeIn"/>

</div>
