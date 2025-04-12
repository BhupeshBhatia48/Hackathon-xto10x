# Hackathon-xto10x
# 🌦️ Weather Forecasting with Machine Learning & Supaboard Dashboard

This project aims to develop a machine learning model for weather forecasting, automate data ingestion and updates, and visualize the forecast insights on a Supaboard dashboard. The goal is to provide real-time weather predictions and trends.

📌 Problem Statement
Weather forecasting is essential for various industries, but predicting weather conditions is challenging due to rapidly changing variables like temperature, humidity, wind speed, and precipitation. In this project, we leverage machine learning to predict key weather metrics and visualize them in an intuitive, user-friendly dashboard.

# Important Info 

1.*"PLEASE UPLOAD THE CSV FILE IN THE COLAB BECAUSE AS THE SESSION ENDS THEY GET RESET"*

2.*"RUN THE CODE ACCORDINGLY"*

3.*"AS RECENT YEARS DATASET CONTAINING ALL THOSE ATTRIBUTES WAS NOT AVAILABLE THATS WHY WE USE OLDER DATASET WHICH AFFECTS THE MSE"*

4.*"ABOVE PROBLEM CAN BE SOLVED BY USING CONTINOUS API INTEGRATION OF WEATHER DATA"*

# 📂 Content Breakdown
The project consists of three main components:
1. **ML Model for Weather Forecasting**
   - A supervised learning model will predict key weather metrics which includes Temperature, Humidity, Wind Speed, Wind Direction, Visibility, Cloud Cover, Pressure.
   - Historical weather data (from 2006-2016) will be used to train and validate the model.

2. **Scheduler for Regular Data Updates**
   - A task scheduler will ingest new weather data from APIs(OpenWeather)at regular intervals.
   - The model will automatically retrain and refine based on the updated data.

3. **Supaboard Dashboard** (https://app.supaboard.ai/data-view/ashish-rangabatla-s-teamspace-data-store--postgres/ashish-rangabatla-s-teamspace/weather-test-1)
   - We used supaboard opensource website for our analytics instead of custom streamlit.
   - Users can view real-time predictions, historical data.

## 🧠 Models Used
- **Supervised Learning Models**: 
  - Regression models (Linear Regression)
  - Fully Connected Neural Network(FCNN) also known as Multilayer Perception(MLP).
  
## 🗃️ Dataset
The dataset contains weather data with the following columns:
- `Date-Time`: (date-time)Timestamp of the weather observation.
- `Temperature`: (numeric) Recorded temperature.
- `Humidity`: (numeric) Humidity percentage.
- `Wind Speed`: (numeric) Wind speed in m/s or km/h.
- `Wind Direction`: (numeric) Wind direction in degrees.
- `Pressure`: (numeric) Atmospheric pressure in hPa.
- `Cloud coverage`: (numeric) Cloud coverage percentage.

### Output Variable:
- `forecasted_weather`: The predicted weather for a future time, which could be either numeric (temperature, humidity) or categorical (weather conditions like rain, snow, etc.).

## 🛠️ Tech Stack
- **Programming Languages**: Python
- **Libraries**: 
  - Scikit-learn, TensorFlow / Keras (for ML models)
  - Pandas, NumPy (data processing)
  - Matplotlib(visualization)
  - Standard scaler(scaling)
  - Mean Squared error & Mean Absolute Error
  - Supaboard (for dashboard visualization)
  - APIs:  Weather data APIs(OpenWeatherMap)

## 📦 Project Overview
- This model is trained of an historic data and in such a way that it will analyse past trends and predict current temperature.
- API key is used to update the past data in real-time for maintaining the quality of the output in future.
- Other than MLP approach like LSTM will be good if we have sequential data of last year or past few years but the dataset we had is from 2006 to 2016 due to this LSTM    cannot make sense of that data in 2025 as it expects a sequential data so after a lot of tries for a suitable dataset we dropped LSTM idea although error was very       less in this model we switched to MLP.
- This model appends the new data into the older data for better learning of the model and making it robust.

# Project Structure
- Data cleaning -> Scaling Features -> Model Training -> Predicting through date-time -> API integration and scheduler -> Comparison with real data -> Analysis on Supaboard dashboard.
# Demo/Presentation
- https://drive.google.com/drive/folders/12bfQ8viHf5UGEgq3sJk81NsNwBIetEqk?usp=sharing

## Limitations and Future Work
- *Scheduling:* The automated scheduling component mentioned in the project context (using cron, Airflow, etc.) is not implemented in this script. This would be                         required for regular, automated data updates and model retraining.
- *Dashboard:* The Supaboard dashboard visualization is not implemented. Integrating the predictions and data with a dashboarding tool (like Supaboard, Streamlit,                      Plotly Dash, etc.) is a future step.
- *Feature Engineering:* The model currently uses only hour, day, and month as input features. Incorporating more features (e.g., lagged weather variables, location                              data if applicable, cyclical encoding of time features) could improve accuracy.
- *Model Complexity:* Explored more advanced time-series models like LSTMs or GRUs might capture temporal dependencies better than a simple feed-forward network.
- *Error Handling:* More robust error handling can be added, especially around API calls and file operations.
- *Configuration:* API keys and other settings could be moved to a separate configuration file or environment variables.
- *Precipitation Type:* The inference of 'Precip Type' from the summary is basic and may not be accurate for all conditions.
