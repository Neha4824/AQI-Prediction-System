# AQI Prediction System
A machine learning-powered web application that predicts the Air Quality Index (AQI) from pollutant measurements and displays the corresponding air-quality category.
The project uses a Random Forest regression model trained on historical air-quality data and is designed to provide an accessible, web-based prediction experience.

## Project Overview
Air pollution monitoring is important for understanding environmental conditions and supporting informed decisions. This project uses machine learning to estimate AQI based on pollutant concentrations and selected time-related features.
Users can enter pollutant values through a web interface and receive:
- Predicted AQI value
- AQI category
- Simple interpretation of the predicted air quality
The project combines data analysis, machine learning, backend API development, and frontend deployment.

## Key Features
- Predicts AQI using a trained Random Forest regression model
- Accepts pollutant measurements as input
- Supports city-based prediction
- Displays the predicted AQI and air-quality category
- Provides a simple and responsive web interface
- Uses a Python backend to serve the machine learning model
- Supports online deployment through GitHub, Render, and Netlify
- Stores the trained model as a `.pkl` file
- Includes model evaluation and performance analysis

## Machine Learning Model
The model was trained using historical city-level air-quality data.

### Input Features
The model uses the following features:
- City
- PM2.5
- PM10
- NO
- NO2
- NOx
- NH3
- CO
- SO2
- O3
- Benzene
- Toluene
- Xylene
- Year
- Month
`AQI` is used as the target variable.
`AQI_Bucket` is not used as an input feature because it is derived from AQI and could cause target leakage.

### Model Comparison
| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | 30.08 | 56.95 | 0.8229 |
| Gradient Boosting | 23.29 | 43.37 | 0.8973 |
| Random Forest | 20.48 | 40.35 | 0.9111 |

### Final Model
The Random Forest regression model was selected based on its test-set performance.
- **MAE:** 20.48 AQI points
- **RMSE:** 40.35 AQI points
- **R² Score:** 0.9111
The R² score indicates that the model explains approximately 91.1% of the variation in AQI on the test dataset. It should not be interpreted as prediction accuracy.

## AQI Categories
The application uses the following AQI category ranges:
| AQI Range | Category |
|---:|---|
| 0–50 | Good |
| 51–100 | Satisfactory |
| 101–200 | Moderate |
| 201–300 | Poor |
| 301–400 | Very Poor |
| Above 400 | Severe |

## Project Architecture
User
  │
  ▼
Netlify Frontend
HTML + CSS + JavaScript
  │
  ▼
Render Backend
Flask API
  │
  ▼
Random Forest Model
aqi_prediction_model.pkl
  │
  ▼
Predicted AQI and Category
  │
  ▼
Result displayed on the website
