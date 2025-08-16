
# Wind Turbine Power Prediction using SCADA Data

## 📖 About the Dataset

This dataset is collected from a **Wind Turbine SCADA system** operating in Turkey.

* Measurements are recorded at **10-minute intervals**.
* Key variables include:

  * **Wind Speed (m/s)**
  * **Wind Direction (°)**
  * **Generated Power (kW)**
  * **Theoretical Power Curve (kWh)**

The goal is to **develop a high-accuracy machine learning model** to predict and optimize turbine output power.

---

## 🎯 Project Objective

1. Perform **Exploratory Data Analysis (EDA)** and feature engineering.
2. Create new features (Season, Day/Night, Temperature, Effective Theoretical Power, etc.).
3. Train and evaluate multiple regression models.
4. Identify the **best-performing model** and tune hyperparameters.

---

## 🛠️ Feature Engineering

The following new features were engineered:

* **Time-based features**: Week, Month, Hour, Season
* **Day/Night** classification (using `astral` & Izmir location)
* **Temperature (°C)** feature (using `meteostat` API)
* **Effective Theoretical Power** (adjusted based on wind direction deviation)

---

## 📊 Data Insights

* **Cut-in speed**: 3.0 m/s
* **Rated velocity**: 17.9 m/s
* Negative power outputs were replaced with **zero**.
* Seasonal and temporal variations in power generation were captured.

---

## 🤖 Models Evaluated

Multiple regression models were tested:

* Gradient Boosting Regressor
* Support Vector Regressor (SVR)
* Random Forest Regressor
* Extra Trees Regressor
* Decision Tree Regressor
* Linear Regression
* AdaBoost Regressor
* XGBRegressor ✅
* XGBRFRegressor
* CatBoost Regressor ✅

---

## 🏆 Results

| Model                   | R² Score (%) | RMSE  |
| ----------------------- | ------------ | ----- |
| **XGBRegressor**        | **97.82**    | 0.146 |
| CatBoost Regressor      | 97.75        | 0.149 |
| Extra Trees Regressor   | 97.49        | 0.158 |
| Random Forest Regressor | 97.01        | 0.172 |

**Best Model after Hyperparameter Tuning:**

* **XGBRegressor**

  * R² = **98.2%**
  * RMSE = **0.13**

---

## ⚡ Key Takeaways

* **Yaw system analysis**: No strong evidence of yaw system influence; high wind speeds occur at specific angles.
* **Feature engineering** significantly boosted accuracy.
* **Temperature feature** (approx. for Izmir) improved model accuracy, though not ideal without exact turbine location.
* **Final tuned XGBoost model** achieved **R² = 98.2%**, making it highly reliable for prediction.

---

## 📂 Repository Structure

```
├── README.md                # Project Documentation  
├── notebooks/               # Jupyter notebooks for EDA & modeling  
├── data/                    # Dataset (if shared) or download instructions  
├── src/                     # Python scripts for preprocessing & training  
├── requirements.txt         # Dependencies  
```

---

## 🚀 How to Run

1. Clone the repo:

   ```bash
   git clone https://github.com/<your-username>/wind-turbine-power-prediction.git
   cd wind-turbine-power-prediction
   ```
2. Install requirements:

   ```bash
   pip install -r requirements.txt
   ```
3. Run the notebook/script to train the model.

---

## 📌 Disclaimer

* The **temperature feature** is approximate (Izmir region) and may not be accurate for the exact turbine location.
* For deployment, local atmospheric and geographic corrections are recommended.

---

## ✨ Future Work

* Deploy trained model with **real-time SCADA data streaming**.
* Test with turbines from **different geographic locations**.
* Explore **deep learning models (LSTM/GRU)** for time-series forecasting.

---

