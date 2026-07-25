# 🔋 Battery Remaining Useful Life (RUL) Prediction using XGBoost

## 📌 Project Overview

This project predicts the **Remaining Useful Life (RUL)** of lithium-ion batteries using Machine Learning. The objective is to estimate the number of charge-discharge cycles a battery can continue operating before reaching its end of life.

Several regression models were trained and compared, and **XGBoost** achieved the best performance after hyperparameter tuning.

---

## 🎯 Problem Statement

Battery degradation is a major challenge in electric vehicles, renewable energy storage, and portable electronic devices. Accurately predicting the Remaining Useful Life (RUL) helps improve maintenance planning, reduce unexpected failures, and increase battery reliability.

This project builds an end-to-end machine learning pipeline to predict battery RUL using operational battery parameters.

---

## 📂 Dataset

- **Dataset:** NASA Battery Aging Dataset
- **Target Variable:** Remaining Useful Life (RUL)

### Features

- Cycle
- Capacity
- Avg Voltage
- Avg Current
- Avg Temperature
- Discharge Time

---

## 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Joblib
- Jupyter Notebook

---

## 📊 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Dataset overview
- Missing value analysis
- Duplicate value removal
- Statistical summary
- Capacity degradation analysis
- Histogram
- Boxplots
- Correlation Heatmap
- RUL Distribution

---

## 🤖 Machine Learning Models

The following regression models were trained and evaluated:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor
- XGBoost Regressor

Hyperparameter tuning was performed using **GridSearchCV**.

---

## 📈 Model Performance

| Model | MAE | RMSE | R² Score |
|--------|-----:|------:|---------:|
| Linear Regression | 28.7185 | 36.7918 | 0.3546 |
| Decision Tree | 2.3836 | 12.7887 | 0.9220 |
| Random Forest | 2.5151 | 8.7082 | 0.9638 |
| Gradient Boosting | 4.4826 | 9.3637 | 0.9582 |
| XGBoost | 2.9507 | 7.2216 | 0.9751 |
| **Tuned XGBoost** ⭐ | **2.7671** | **6.3863** | **0.9806** |

---

## ⭐ Best Model

**Tuned XGBoost**

Performance:

- MAE: **2.7671**
- MSE: **40.7845**
- RMSE: **6.3863**
- R² Score: **0.9806**

The tuned XGBoost model achieved the highest prediction accuracy and was selected as the final model.

---

## 📊 Visualizations

The project includes:

- Capacity Degradation Curve
- Correlation Heatmap
- Feature Importance Plot
- Actual vs Predicted Plot
- Residual Plot

---

## 💾 Model Deployment Preparation

The trained XGBoost model was saved using **Joblib** for future predictions.

```python
joblib.dump(best_xgboost, "battery_rul_xgboost_model.pkl")
```

---

## 🔮 Sample Prediction

Example battery:

| Feature | Value |
|---------|------:|
| Cycle | 120 |
| Capacity | 1.45 |
| Avg Voltage | 3.42 |
| Avg Current | -1.85 |
| Avg Temperature | 34.5 |
| Discharge Time | 2950 |

**Predicted Remaining Useful Life**

**56.33 Cycles**

---

## 📁 Project Structure

```
Battery-RUL-Prediction-using-XGBoost
│
├── Battery_RUL_Prediction.ipynb
├── battery_rul_dataset.csv
├── battery_rul_xgboost_model.pkl
├── requirements.txt
├── README.md
└── images
```

---

## 🚀 Future Improvements

- Train deep learning models (LSTM/GRU)
- Use larger battery datasets
- Deploy using Streamlit or Flask
- Integrate with Battery Management Systems (BMS)
- Real-time battery health monitoring

---

## 📚 References

- NASA Prognostics Center of Excellence Battery Dataset
- Scikit-learn Documentation
- XGBoost Documentation

---

## 👨‍💻 Author

**Omkar Kavathekar**

Electrical Engineering Student | Machine Learning Enthusiast

GitHub: https://github.com/okavthekar-dev

LinkedIn: https://linkedin.com/in/omkar-kavathekar

---

⭐ If you found this project helpful, consider giving it a star!
