# 📊 Sampling Techniques on Imbalanced Credit Card Dataset
### Handling Class Imbalance Using Oversampling (SMOTE)

---

## 🔍 Project Overview

In real-world machine learning applications, datasets are often **highly imbalanced**, where one class significantly dominates the other. This imbalance can severely degrade model performance, especially for critical tasks such as **fraud detection**.

This project focuses on:
- Analyzing an imbalanced credit card transaction dataset
- Visualizing class imbalance
- Applying **SMOTE (Synthetic Minority Oversampling Technique)**
- Demonstrating how oversampling improves class distribution and model reliability

---

## 🎯 Objectives

- To analyze class imbalance in the dataset  
- To visualize class distribution before and after balancing  
- To apply SMOTE oversampling to balance the dataset  
- To improve model learning by eliminating class bias  
- To present clear visual evidence suitable for academic evaluation  

---

## 📁 Dataset Description

- **Dataset Name:** Creditcard_data.csv  
- **Problem Type:** Binary Classification  
- **Target Column:** `Class`  
  - `0` → Non-Fraud Transaction  
  - `1` → Fraud Transaction  
- **Challenge:** Extreme imbalance (fraud cases are very rare)

---

## 📊 Class Distribution Analysis

Before applying any balancing technique, the dataset is **severely skewed** toward non-fraud transactions. This causes machine learning models to favor the majority class and ignore fraudulent cases.

To address this issue, **SMOTE oversampling** is applied to synthetically generate minority-class samples.

---

## 🖼️ Before vs After SMOTE Oversampling

The following visualization clearly illustrates the effect of SMOTE on class distribution:

![Before and After SMOTE](images/before_after_smote.png)

### 🔹 Interpretation of the Visualization

- **Before Balancing:**  
  - Class `0` (Non-Fraud) dominates the dataset  
  - Class `1` (Fraud) has very few samples  
  - Models trained on this data are biased

- **After SMOTE:**  
  - Both classes have **equal representation**  
  - Dataset becomes balanced (50% fraud, 50% non-fraud)  
  - Models can now learn patterns from both classes fairly  

---

## 🧠 Why SMOTE?

SMOTE improves learning by:
- Preserving all majority-class data  
- Generating synthetic minority samples instead of duplicating data  
- Reducing model bias  
- Improving generalization and predictive accuracy  

> SMOTE is preferred over undersampling because it avoids information loss.

---

## 📈 Key Insights

- Severe class imbalance exists in raw credit card data  
- Visual analysis confirms minority class under-representation  
- SMOTE successfully balances the dataset  
- Balanced data leads to improved model performance and fairness  

---

## 📂 Repository Structure

