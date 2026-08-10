# 🔋 Battery RUL Prediction

A machine learning project for predicting the **Remaining Useful Life (RUL)** of lithium-ion batteries using battery cycling and operating characteristics.

## 📌 Project Overview

Remaining Useful Life (RUL) represents the number of cycles a battery can continue operating before reaching its end-of-life condition.

The goal of this project is to develop a machine learning model that can predict battery RUL and, more importantly, evaluate how well the model generalizes to **completely unseen batteries**.

---

## 📊 Dataset

The project uses battery aging data derived from **NASA battery degradation experiments**.

The dataset is **not included in this repository**. The notebooks contain the preprocessing and feature construction steps used to prepare the modeling dataset.

The final modeling data contains battery-level cycling and operating characteristics such as:

- `Battery_ID`
- `Cycle`
- `Capacity`
- `Avg_Voltage`
- `Avg_Current`
- `Avg_Temperature`
- `Discharge_Time`
- `RUL`

---

## 🔍 Exploratory Data Analysis

The dataset was explored to understand:

- Battery capacity degradation
- Relationship between cycle number and RUL
- Voltage, current and temperature behavior
- Battery-wise degradation patterns
- Feature correlations

Several visualizations were used to understand the degradation behavior and relationships between the input features and RUL.

---

## ⚙️ Feature Engineering

Feature engineering was performed to better represent battery degradation behavior.

The engineered features included capacity-based and rolling features such as:

- Initial capacity
- Capacity ratio
- Capacity degradation
- Capacity change
- Rolling statistics

These features were evaluated to determine whether they improved the model's ability to generalize to unseen batteries.

---

## ⚠️ Investigating the Unexpectedly High R²

The feature-engineered model achieved an unusually high R² score of **1.0000** during GroupKFold validation.

Since RUL was calculated as:

**RUL = Maximum Cycle − Current Cycle**

the target is directly related to the cycle number.

This indicated that the validation setup could be making the prediction task unrealistically easy.

Therefore, instead of relying on the perfect score, the evaluation was redesigned to test the model on **completely unseen batteries**.

This provides a more realistic assessment of the model's ability to generalize to new battery degradation patterns.

---

## 🔬 Battery-wise Train/Test Split

The dataset was divided into:

- **27 training batteries**
- **7 completely unseen testing batteries**

The model was trained only on the training batteries and evaluated on the testing batteries.

This prevents observations from the same battery appearing in both training and testing sets and provides a more realistic evaluation of RUL prediction.

---

## 🔄 GroupKFold Validation

GroupKFold validation was used during model development to ensure that observations belonging to the same battery were kept within the same fold.

The battery ID was used as the grouping variable.

This helps prevent information from the same battery from being shared between training and validation data.

---

## 🤖 Models Evaluated

The following regression models were evaluated:

- Linear Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- XGBoost
- Extra Trees

The models were evaluated using:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² Score

---

## 📈 Model Comparison

The models were evaluated on the **7 completely unseen batteries**.

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 51.6898 | 88.4712 | -7.4142 |
| Decision Tree | 10.6588 | 29.8692 | 0.0409 |
| Random Forest | **9.6968** | **18.4213** | **0.6352** |
| Gradient Boosting | 15.1494 | 24.2516 | 0.3677 |
| XGBoost | 10.3473 | 18.8648 | 0.6174 |
| Extra Trees | 10.0039 | 18.8614 | 0.6176 |

Random Forest achieved the best overall performance on the unseen-battery test set.

---

## 🎯 Final Model

The final selected model is:

**Random Forest Regressor**

### Performance on 7 unseen batteries

| Metric | Score |
|---|---:|
| MAE | **9.6968 cycles** |
| RMSE | **18.4213 cycles** |
| R² | **0.6352** |

The model explains approximately **63.5% of the variance in RUL** on the completely unseen test batteries.

The final model was selected based on its overall generalization performance rather than the highest score obtained during earlier experiments.

---

## 🔧 Hyperparameter Tuning

Hyperparameter tuning was performed for both Random Forest and XGBoost to investigate whether their performance could be improved.

### Tuned Random Forest

The tuned Random Forest achieved:

- MAE: 12.1304
- RMSE: 20.7009
- R²: 0.5393

This was worse than the original Random Forest.

### Tuned XGBoost

The tuned XGBoost achieved:

- MAE: 10.1798
- RMSE: 19.3837
- R²: 0.5961

This was also lower than the original Random Forest.

Therefore, the original Random Forest model was retained as the final model.

---

## 🔬 Battery-wise Error Analysis

Performance varied between individual batteries because different batteries can exhibit different degradation patterns.

Battery-wise evaluation showed that the model performed very well on some batteries while showing larger errors on others.

For example, larger errors were observed for batteries such as **B0049** and **B0050**.

This highlights the difficulty of generalizing RUL predictions across batteries with different aging characteristics.

---

## 📊 Model Interpretation

Feature importance was analyzed to understand which battery characteristics contributed most to the Random Forest predictions.

This provides insight into which degradation and operating characteristics are most useful for estimating remaining useful life.

---

## 💾 Saved Model

The final Random Forest model was saved using **Joblib**.

```text
models/battery_rul_random_forest.pkl


---

## 👤 Author

**Omkar Kavathekar**
