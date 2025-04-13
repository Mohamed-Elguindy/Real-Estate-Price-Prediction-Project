# 🏠 Real Estate Price Prediction — Bengaluru

This project predicts real estate prices in Bengaluru using linear regression. It includes thorough data preprocessing, outlier detection, feature engineering, and model deployment logic.

---

## 📌 Objectives

- Clean and preprocess real estate data.
- Engineer features like BHK, price per sqft, etc.
- Remove outliers based on domain knowledge and statistics.
- Train a machine learning model to predict housing prices.
- Provide a custom prediction function for new data.

---

## 📂 Dataset

- **Source**: `bengaluru_house_prices.csv`
- **Main Features**:  
  `location`, `size`, `total_sqft`, `bath`, `balcony`, `price`

---

## ⚙️ Technologies

- Python 3  
- Jupyter Notebook  
- Pandas, NumPy, Matplotlib  
- Scikit-learn (Linear Regression)  

---

## 📈 Workflow Summary

### 1. **Data Cleaning**
- Dropped unused columns like `area_type`, `availability`, `society`
- Filled missing values in `bath` and `balcony` using median

### 2. **Feature Engineering**
- Extracted `BHK` from `size` column
- Converted `total_sqft` to numeric values (including ranges)
- Created `price_per_sqft` and `area_per_bhk` features
- Encoded `location` using one-hot encoding

### 3. **Outlier Removal**
- Removed:
  - Rows where area per BHK < 300 sqft
  - BHK outliers where higher BHK has lower price/sqft than lower BHK
  - Price per sqft outliers per location

### 4. **Visualization**
- Scatter plots comparing 2 BHK vs 3 BHK prices for specific locations
- Histogram of price per sqft

### 5. **Model Training**
- Used **Linear Regression** model
- Train-test split (80/20)
- Model evaluation using `.score()` method

### 6. **Price Prediction Function**
Custom function:
```python
predict_price(location, sqft, bath, balcony, bhk)
```
Returns estimated price for the given configuration.

---

## 🧪 Example Predictions
```python
predict_price('1st Phase JP Nagar', 1000, 2, 1, 2)  # ~83.8 Lakhs
predict_price('1st Phase JP Nagar', 1200, 3, 1, 3)  # ~89.8 Lakhs
```
