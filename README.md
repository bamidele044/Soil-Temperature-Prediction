# Soil Temperature Prediction at Carrigeen, Co. Waterford, Ireland

### Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Data Source](#data-source)
- [Tool and Libraries](#tool-and-libraries)
- [Data Preprocessing and Handling Missing Values](#data-preprocessing-and-handling-missing-values)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Univariate Analysis](#univariate-analysis)
- [Bivariate Analysis](#bivariate-analysis)
- [Time Series Preparation and Stationarity Testing](#time-series-preparation-and-stationarity-testing)
- [Stationarity Analysis (ADF Test)](#stationarity-analysis-adf-test)
- [Splitting Dataset into Training and Testing](#splitting-dataset-into-training-and-testing)
- [Model Development](#model-development)
- [Model Evaluation](#model-evaluation)
- [Model Performance Summary](#model-performance-summary)
- [Practical Applications](#practical-applications)
- [Conclusion](#conclusion)
- [Recommendations](#recommendations)
- [References](#references)

### Project Overview
---
Soil temperature is a critical environmental factor affecting agriculture, climate modeling, and ecosystem sustainability. Accurate prediction of soil temperature helps in optimizing farming practices and understanding climate trends. This project explores various machine learning models to develop a robust soil temperature prediction system for Carrigeen, Co. Waterford, Ireland.

### Problem Statement
Soil temperature is influenced by multiple factors, including air temperature, solar radiation, and moisture content. Accurately predicting soil temperature is essential for agricultural planning and climate modeling. This project analyzes meteorological factors affecting soil temperature and develops machine learning models that aim to outperform traditional statistical methods in predictive accuracy.

### Data Source
The dataset used in this project was provided as part of an academic course.

### Tool and Libraries
- Programming Language: R
- Libraries Used:
  - `caret` (machine learning and model training)
  - `corrplot` (correlation matrix visualization)
  - `dplyr` (data manipulation)
  - `e1071` (SVM)
  - `forecast` (time series analysis)
  - `ggplot2` (data visualization)
  - `gridExtra` (arranging multiple ggplot2 plots)
  - `lubridate` (working with date and time)
  - `randomForest` (machine learning)
  - `reshape2` (data reshaping)
  - `rpart` (decision tree modeling)
  - `tidyverse` (collection of data science packages)
  - `tseries` (stationarity tests like ADF)

### Data Preprocessing and Handling Missing Values
- Handling Missing Data
  - Before performing Exploratory Data Analysis (EDA), missing values were identified and handled appropriately.
  - Missing values were replaced using mean imputation to maintain data integrity.
  - Non-numeric columns were converted to numeric where necessary.

### Exploratory Data Analysis (EDA)
- Data Overview
The dataset includes soil temperature readings and meteorological variables such as air pressure, wind components, humidity, and precipitation. The dataset was filtered to focus on a specific location (latitude: 52.242, longitude: -7.4) with 300 observations extracted around the matched row.

### Univariate Analysis
- Histogram of Soil Temperature

On X01.05.2018 00.00, the soil temperature distribution shows a dominant peak at around 273 K, with frequency exceeding 200. This suggests that most soil measurements were concentrated around this temperature, while higher temperatures were less frequent.

![Screenshot (101)](https://github.com/user-attachments/assets/f306222a-29e4-46c1-bc2e-c3b26877b557)

### Bivariate Analysis
- Correlation Matrix

Key insights from correlation analysis:
- A strong positive correlation (0.96) between soil temperature and air temperature.
- A strong negative correlation (-0.91) between soil temperature and soil moisture.

![Screenshot (103)](https://github.com/user-attachments/assets/9a573641-2c0b-4d04-8462-7e70075c08e7)


### Time Series Preparation and Stationarity Testing
- Time Series Data Preparation
  - A `DATETIME` column was created, ranging from May 1, 2018, to May 31, 2018, at 3-hour intervals.
  - The dataset was structured for time series modeling, ensuring correct indexing.

### Stationarity Analysis (ADF Test)
To check for stationarity, the Augmented Dickey-Fuller (ADF) test was performed. The null hypothesis (H₀) states that the data is non-stationary.

#### Results (Before Differencing):
- p-value: 0.36
- Interpretation: Since the p-value is greater than 0.05, we fail to reject H₀, indicating the time series is non-stationary.
 
![Screenshot (104)](https://github.com/user-attachments/assets/b593d8d1-2aea-49e8-ba9b-88df1074c00e)

Since the series was non-stationary, first-order differencing was applied, and the ADF test was repeated.

#### Results (After Differencing):
- p-value: 0.01
- Interpretation: Since the p-value is less than 0.05, we reject H₀, confirming that the series is now stationary.

![Screenshot (105)](https://github.com/user-attachments/assets/fa3a508f-df3b-47cd-bb37-393d6bfb1104)


### Splitting Dataset into Training and Testing
- After conducting the ADF test and confirming stationarity, the dataset was split into training (70%) and testing (30%) sets to ensure model evaluation was based on unseen data.
- The training set was used for model development, while the testing set was reserved for performance evaluation.

### Model Development
Several models were evaluated for predicting soil temperature:
- Linear Regression (LM)
- Support Vector Regression (SVR) with different kernels (Radial, Linear, Polynomial)
- Decision Tree (DT)
- Random Forest (RF) with 100, 200, and 500 trees
- ARIMA

### Model Evaluation
Root Mean Squared Error (RMSE) was used to compare model performance.

![Screenshot (106)](https://github.com/user-attachments/assets/fb441819-c416-4a7b-b6db-1660f330a983)

### Model Performance Summary
|Model|RMSE|
|-----|----|
|Linear Regression|2.517296|
|SVR (Radial)|2.519932|
|SVR (Linear)|2.520215|
|SVR (Polynomial)|2.525582|
|Decision Tree|2.608039|
|Random Forest (100 trees)|2.92076|
|Random Forest (200 trees)|2.959271|
|Random Forest (500 trees)|2.9418|
|ARIMA|2.600654|

The Linear Regression model had the lowest RMSE (2.517), making it the best predictor for soil temperature.

### Practical Applications
The results of this study have significant applications in:
- Agriculture: Farmers can optimize irrigation schedules and crop selection based on predicted soil temperature.
- Climate Research: Predicting soil temperature aids in assessing climate change impacts on local ecosystems and agricultural productivity.

### Conclusion
This study successfully developed predictive models for soil temperature at Carrigeen, Co. Waterford, Ireland. Linear Regression emerged as the most accurate model. The findings can be leveraged for agricultural planning and climate monitoring, highlighting the importance of data-driven decision-making in environmental sciences.

### Recommendations
To further improve predictive accuracy and expand the practical applications of this study, the following recommendations are proposed:
- Enhancing Model Performance:
  - Explore deep learning techniques such as LSTMs (Long Short-Term Memory Networks) for better time-series forecasting
  - Expand the dataset to include additional meteorological variables (e.g., soil type, wind patterns) for improved predictions.

- Integration into Decision-Making Systems:
  - Incorporate the model into agricultural decision-support systems to assist farmers in real-time decision-making.
  - Develop a web or mobile-based application to provide easy access to soil temperature predictions for farmers and researchers.

### References

Anon. (2018). [click here](https://medcraveonline.com/APAR/APAR-08-00288.pdf0)

Anon. (2023). [click here](https://eos.com/blog/soil-temperature/)

Santra, R. (2023). [click here](https://medium.com/@ritusantra/stationarity-in-time-series-887eb42f62a9)

Velicer, W. and Fava, J. (2003). [click here](https://www.researchgate.net/publication/229633091_Time_Series_Analysis)










