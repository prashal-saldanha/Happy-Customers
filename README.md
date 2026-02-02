# 😊 Happy Customers – Customer Satisfaction Prediction

## 📌 Project Overview

This project focuses on predicting **customer happiness** based on their responses to a short post-order satisfaction survey for a fast-growing logistics and on-demand delivery startup.

As the company scales globally, maintaining a consistently positive customer experience becomes critical for **growth, retention, and operational efficiency**.

Using structured survey responses, this project builds and evaluates multiple classification models to:

- Predict whether a customer is **happy or unhappy**
- Identify the **key drivers** of customer satisfaction
- Reduce survey complexity by highlighting **low-impact questions**
- Translate analytical insights into **actionable business recommendations**

---

## 🧠 Business Problem

Customer satisfaction reflects multiple operational dimensions such as:

- Delivery timeliness  
- Pricing  
- Courier behavior  
- App usability  

However, understanding **which factors matter most** and which do not is challenging, especially with limited data.

This project aims to shift the business from **reactive problem-solving** to **proactive, data-driven decision-making** by answering:

- What predicts customer happiness?
- Which survey questions are most valuable?
- Can future surveys be simplified without losing insight?

---

## 📊 Data Description

- **Dataset Size:** 126 customer responses  
- **Features:** 6 ordinal survey questions (scale: 1–5)  
- **Target Variable:** Customer happiness (binary)

### Survey Features

| Feature | Description |
|------|------------|
| X1 | Order delivered on time |
| X2 | Order contents as expected |
| X3 | Ability to order everything needed |
| X4 | Satisfaction with price |
| X5 | Satisfaction with courier |
| X6 | App usability |

### Target Variable

- `Y = 1` → Happy customer  
- `Y = 0` → Unhappy customer  

The dataset is **well balanced**, with slightly more happy customers than unhappy ones, making it suitable for classification modeling.

---

## 🎯 Project Goals

### Primary Goal
Build a **binary classification model** that predicts customer happiness with acceptable accuracy.

### Secondary Goals

- Identify the most influential drivers of happiness  
- Remove or consolidate low-impact survey questions  
- Improve interpretability for business stakeholders  

---

## 📏 Success Metrics

- **Primary Metric:** Classification Accuracy  
- **Target Benchmark:** ≥ **73% accuracy** (given small dataset size)

### Secondary Considerations
 
- Feature importance  
- Generalization vs. overfitting  

---

## 🔍 Project Workflow

### 1️⃣ Data Loading & Inspection

- Loaded survey data and verified data types  
- Confirmed no missing values  
- Reviewed summary statistics and distributions  

---

### 2️⃣ Exploratory Data Analysis (EDA)

**Key Insights:**

#### Customer Happiness Distribution
- Fairly balanced classes (69 happy vs. 57 unhappy)

#### Strong Drivers of Happiness
- **On-time delivery (X1)**
- **Courier satisfaction (X5)**
- **App usability (X6)**

#### Low-Impact Factor
- **Order accuracy (X2)** shows minimal relationship with happiness

#### Correlation Analysis
- X1, X5, and X6 show the strongest positive correlation with happiness  
- X2 shows near-zero correlation  
- No severe multicollinearity among features  

📌 **Insight:** Customers are more sensitive to the **delivery experience and convenience** than minor order inaccuracies.

---

### 3️⃣ Model Training & Evaluation

Six classification models were trained and compared:

- Logistic Regression  
- Support Vector Machine (SVM)  
- Random Forest  
- Decision Tree  
- XGBoost  
- k-Nearest Neighbors (KNN)  

**Evaluation Strategy**
- Train–test split with stratification  
- Accuracy, ROC-AUC, and confusion matrices  
- Overfitting vs. generalization analysis  

---

### 4️⃣ Model Performance Summary

| Model | Validation Accuracy | Key Observation |
|-----|--------------------|----------------|
| Logistic Regression | 71.9% | Strong baseline, high interpretability |
| SVM | 71.9% | Best balance of performance and stability |
| Random Forest | 68.8% | Overfitting due to small dataset |
| Decision Tree | 65.6% | Moderate overfitting |
| XGBoost | 56.3% | Poor generalization |
| KNN | 68.8% | Lower ROC-AUC |

📌 **Conclusion:**  
- **SVM** is the most reliable model  
- Complex tree-based models overfit with limited data  

---

### 5️⃣ Feature Selection

Two complementary techniques were applied:

#### 🔹 L1-Regularized Logistic Regression

**Important Features**
- X1 – On-time delivery  
- X3 – Order completeness  
- X5 – Courier satisfaction  

**Low-Impact Features**
- X2 – Order accuracy  
- X4 – Price satisfaction  
- X6 – App usability  

#### 🔹 Recursive Feature Elimination (RFE)

- **Optimal feature count:** 2  
- **Selected features:**
  - X1 – On-time delivery  
  - X3 – Order completeness  

📌 **Consistent Insight:**  
**On-time delivery (X1)** is the single most influential driver of customer happiness.

---

### 6️⃣ Final Models with Feature Selection

| Model | Accuracy | Recommendation |
|-----|---------|----------------|
| Logistic Regression + RFE | 61% | ❌ Not recommended |
| SVC + RFE | 73% | ✅ Recommended |

---

## 🚀 Deployment Recommendation

**Deploy:**  
👉 **Support Vector Classifier (SVC)** using **X1 and X3**

### Why this model?
- Meets performance benchmark  
- Uses minimal features  
- Reduces survey fatigue  
- Easy to maintain and scale  

---

## 💡 Business Impact & Insights

### Operational Focus Areas
- Improve delivery timeliness  
- Ensure customers can order everything they need  

### Survey Optimization
- Remove or merge low-impact questions  
- Shorter surveys → higher response rates  

### Strategic Value
- Enables proactive customer experience management  
- Aligns analytics directly with business priorities  

---

## 🏁 Final Thoughts

This project demonstrates:

- Translate business problems into analytical solutions  
- Balance model performance and business impact  
- Communicate insights clearly to non-technical stakeholders  

Rather than maximizing complexity, this work emphasizes **practical decision-making**, **feature relevance**, and **real-world usability**.
