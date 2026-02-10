# Data Generation Using Modelling and Simulation for Machine Learning

## Overview

This project demonstrates synthetic data generation using modelling and simulation and its application to machine learning. Cantera is used to simulate a gas system under varying temperature and pressure. The generated thermodynamic property (Specific Heat) is treated as labeled data for ML model training and comparison.

---

## Methodology

### 1. Simulation Setup

Cantera (`gri30.yaml`) is used to model a reacting gas mixture in equilibrium.

Two input parameters are randomly varied:

| Parameter | Range |
|-----------|-------|
| Temperature | 800–1500 K |
| Pressure | 1–10 atm |

For each parameter set:

- Cantera computes thermodynamic properties  
- **Specific Heat (cp)** is extracted as output  

A total of **1000 simulations** are executed to generate synthetic data.

---

### 2. Dataset Construction

Generated dataset columns:

- `Temperature_K` – input feature  
- `Pressure_atm` – input feature  
- `Specific_Heat` – output label  

The dataset is saved as `cantera_simulated_data.csv`.

---

### 3. Data Visualization

Histograms are plotted for:

- Temperature  
- Pressure  
- Specific Heat  

These plots confirm uniform sampling and continuous physical output variation.

---

### 4. Machine Learning

The dataset is split into 80% training and 20% testing.

Five regression models are trained:

- Linear Regression  
- Decision Tree  
- Random Forest  
- Support Vector Regression  
- KNN  

Target variable: **Specific Heat**

---

### 5. Model Evaluation

Models are evaluated using:

- Mean Squared Error (MSE)  
- Mean Absolute Error (MAE)  
- R² Score  

---

## Results

| Model | MSE | MAE | R² |
|------|-----|-----|----|
| Linear Regression | 33.23 | 4.92 | 0.989 |
| Decision Tree | 0.09 | 0.20 | 0.999 |
| Random Forest | **0.03** | **0.13** | **0.9999** |
| SVR | 113.29 | 5.77 | 0.964 |
| KNN | 0.09 | 0.23 | 0.999 |
<img width="567" height="624" alt="image" src="https://github.com/user-attachments/assets/1cbdf633-f2ae-47e8-b703-a448fe0562a8" />

A bar chart visualizes R² scores across models.

**Random Forest Regressor** achieves the best overall performance.

High accuracy is expected because the dataset is generated from deterministic physical equations.

---

## Conclusion

This project demonstrates how modelling and simulation can generate synthetic datasets for machine learning. The simulated physical system provides structured data, and ML models successfully learn the relationship between temperature, pressure, and specific heat.

---

## Author

Samarth Mahajan  
B.Tech Computer Engineering  
