# Airbnb/Hotel Price Prediction using Machine Learning

## Overview

This project analyzes hotel and Airbnb-style lodging data from New York City to uncover trends and insights that can benefit:

- Travelers: to find value-for-money accommodations  
- Hoteliers: to optimize pricing and availability  
- Policymakers: to understand urban tourism dynamics

Using various data science techniques—such as data cleaning, exploratory data analysis (EDA), visualization, and machine learning—it provides actionable insights about availability, pricing, customer ratings, and location.

---

## 📄 Dataset

**The dataset includes comprehensive details on:**

- **Hotel attributes:** Names, types (luxury, budget), classifications  
- **Room details:** Room type, number of beds, availability, minimum nights  
- **Customer feedback:** Reviews, ratings, last review date  
- **Pricing:** Cost per night, per month  
- **Geographic info:** Neighborhood, latitude, longitude  

> *Note:* Rows with `price > 10000` were removed as outliers to improve model accuracy.

---

## Features

### 1. **Data Cleaning**
- Handles missing values and inconsistencies
- Drops irrelevant fields like `name`, `host_name`
- Caps prices and transforms variables like `last_review` to `days_since_last_review`

### 2. **Feature Engineering**
- Adds derived features like `last_review`

### 3. **EDA and Visualization**
- Price distribution across neighborhoods
- Rating vs. price trends to identify value-for-money listings
- Heatmaps showing density of listings in New York

### 4. **Machine Learning Pipeline**
- Models used:
  - Random Forest Regressor 
  - XGBoost Regressor 
  - LightGBM Regressor 
- Model evaluation using:
  - Mean Absolute Error (MAE)
  - Mean Squared Error (MSE)
  - R² Score

---

## 📈 Final Model Performance

| Metric | Value |
|--------|-------|
| **MSE** | 10011.99 |
| **MAE** | 24.73 |
| **R²**  | 0.88 |

✅ The final model explains **88% of the variance** in hotel pricing and predicts with an average error of ~$25.

---

## Tools & Technologies

- **Python**
- **Pandas**, **NumPy** – for data cleaning & analysis  
- **Matplotlib**, **Seaborn**, **Plotly** – for visualizations  
- **scikit-learn** – for ML modeling
- **RandomForestRegressor** - for prediction 
- **Jupyter Notebook** – interactive development  
- **Streamlit** – for building a web-based dashboard  

---

## 💻 Installation & Running the Project

### 📦 Clone the Repository

```bash
git clone https://github.com/jvpurushotham/Hotel-Price-Prediction.git
cd Hotel-Price-Prediction
```

### 📊 Run the Jupyter Notebook

```bash
jupyter notebook NewYorkCity_Hotels_Data_Analysis.ipynb
```

### 🌐 Launch the Streamlit App (optional)

```bash
streamlit run streamlit.py
```

---

## 👤 Author

**Developed by:** [J V Purushotham]  
📧 Email: jvpurushotham31@gmail.com  
🔗 GitHub: [github.com/jvpurushotham](https://github.com/jvpurushotham)
