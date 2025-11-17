# Future of Pricing in Real Estate
A data-driven analysis of housing prices using Python, pandas, scikit-learn, and Seaborn.

## Overview
This project explores real estate pricing trends and identifies the features that influence house prices the most. Using statistical methods and machine-learning models, it predicts home values and compares model performance.

- **Dataset:** [Kaggle – KC Housing Data](https://www.kaggle.com/datasets/shivachandel/kc-house-data)
- **Platform:** Jupyter Notebook  
- **Language:** Python  
- **Libraries:** pandas, numpy, seaborn, scikit-learn, matplotlib

## Project Files

### **All source code and project files are available in the repository’s Code section.**

## Data Preparation Workflow
1. Loaded and reviewed the dataset to understand structure and data types.  
2. Explored numerical features (min, max, mean) to understand data ranges.  
3. Checked and handled missing values in key columns.  
4. Reviewed categorical columns and unique value counts.  
5. Examined whether “floors” and “view” could be combined; distributions were inconsistent, so both were kept separate.  
6. Analyzed correlations to identify highly similar numerical features.  
7. Applied PCA to merge correlated variables and reduce multicollinearity.  
8. Removed the ID column as it has no predictive value.  
9. Bucketed bedrooms, bathrooms, grade, and zipcode into meaningful ranges.  
10. Created dummy variables (one-hot encoding) for all categorical and bucketed features.

## Variable Selection Methods
| Method | Meaning |
|--------|---------|
| Forward Selection (Adj. R²) | Adds variables based on improvement. |
| Backward Elimination (Adj. R²) | Removes least useful variables step-by-step. |
| Random Forest Importance | Ranks feature importance using tree ensembles. |
| RFE | Recursively removes weakest predictors. |
| LASSO | Shrinks coefficients to keep strongest predictors. |

## Predictive Models
| Algorithm | Type | What It Does | When It’s Useful |
|----------|------|--------------|------------------|
| **K-Nearest Neighbors (KNN) Classification** | Classification | Looks at the *k* most similar past observations and predicts the class (e.g., high price vs low price) based on the majority. | When you want simple, distance-based predictions and your features are well-scaled. Great for classification tasks. |
| **Multiple Linear Regression** | Regression | Models the relationship between several input features and a continuous output (price). It finds the best-fitting line through the data. | When you need actual numeric predictions (e.g., dollar price). Works best when relationships are roughly linear. |


## Key Findings

### 1️⃣ Most Important Variables for Predicting Price
- waterfront  
- latitude  
- longitude  
- living_pc (living area % of lot)  
- year built  
- grade  

### 2️⃣ Best K for KNN
| K | Validation Accuracy |
|----|---------------------|
| 5  | 0.8933 |
| 10 | 0.8954 |

➡️ **K = 10 performed best.**

### 3️⃣ Model Comparison
**Multiple Linear Regression**
- R²: 0.60–0.65  
- Predicts exact prices  
- Works well for linear relationships  

**KNN (k = 10)**
- Accuracy: 0.88–0.89  
- Great for classification, not for predicting exact dollars  

**Summary:**  
- Linear Regression → best for predicting dollar price  
- KNN → best for classifying price level  

### Price Predictions for Two Houses
| House | Actual | Predicted | Error | Accuracy |
|--------|---------|------------|--------|-----------|
| House 1 | \$459,000 | \$426,612 | 7.06% | 92.94% |
| House 2 | \$465,000 | \$301,864 | 35.08% | 64.92% |
