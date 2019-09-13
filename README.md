# Markowitz Portfolio Theory Supplemented by Machine Learning

## DISCLAIMER
I highly reccomend you do not use this project as a basis for investing. This project does not aim to create a optimal trading strategy, but rather to demonstrate the feasibility of supplementing investment strategies with machine learning methodologies.

## Executive Summary
The purpose of this project is to explore the promise of machine learning algorithms in combination with financial theory to obtain a optimal portfolio. I do this by tuning and training 3 supervised machine learning models on historical stock price data and fundamental data in order to forecast 1-year-ahead and 2-year-ahead returns. I found that the Random Forest Regressor performs best of the three algorithms in constructing an optimal portfolio. You can find a full written report in this repo.

## Outline
1. Data Set Description
2. Methodology
3. Results and Conclusion
4. Appendix

## 1. Data Set Description

I gathered this dataset using Quandl's API. I used this data because it was free and reasonably accurate. You can find the specific details of how I garthered and processed the data in my Data Wrangling and Cleaning Notebook. You can also find the data gathered in this repo.

The data is composed of two flat files. The first, historical stock closing price data of all the stocks in the S&P 500 from 1999-01-04 until 2018-03-27 – the latter date was determined by the end of the datasets updating. The data was gathered from the Quandl WIKI. The second, fourth quarter fundamental stock data of all the stocks in the S&P 500 from the years 2011 until 2018. The data was gathered from SHARADAR's available test data through the Quandl API.

The missing data is due to stocks not existing publically at certain time periods.

## 2. Methodology

### i. Data Wrangling and Cleaning
All wrangling and cleaning is explained in the wrangling and cleaning notebook. 
This section primarily uses pandas, numpy, and quandl libraries.

### ii. Exploratory Data Analysis
This notebook looks at all 505 stocks composing the S&P 500 as of 2019-05-01. 
I explore the returns of all the stocks, seasonal decomposition of the market average, and correlations between stocks.
This section primarily uses panda, matplotlib, seaborn, and numpy.

### iii. Data Preprocessing
You can find this in the Data Analysis notebook.
- Add annual returns for following year to fundamentals data set
- Create excess returns variable as response variable
- Remove stocks without full dataset
- Split into Train and Test Data
- Create standardized dataset for KNN Algorithm (this is done in the the Model Tuning and Model Testing section)
This section primarily uses pandas and numpy libraries.

### iv. Model Tuning
You can find this in the Data Analysis notebook.
My tuning method uses GridSearchCV from the sklearn library.

### v. Optimal Portfolio Construction
You can find this in the Data Analysis notebook and an explanation of it in the appendix.
We evaluate the efficacy of the model by using its predictions to construct an optimal portfolio. The construction of an optimal portfolio means we are minimizing risk and maximizing return for that level of risk. 
This section uses the numpy library.

### vi. Model Evaluation
You can find this in the Data Analysis notebook.
I compare the performance of the Random Forest Regressor, Gradient Boosting Regressor, and KNN Regressor.
The models are from the xgboost and sklearn libraries.

## 3. Results and Conclusion
The Random Forest Regressor performed the best in both the 1-step-ahead and 2-step-ahead forecasts. It is worth mentioning that the difference in performance of the 2-step-ahead forecast would be due to the dataset potentially becoming outdated, not because the model is accounting for the passage of time.

There are several things I believe I could improve upon this project:
### Data:
- Using a larger dataset including more stocks than just the S&P 500
- Using quarterly data for stocks fundamentals
- Including incomplete stock data in model training
- Including Fama-French Factors data (this is considered the baseline for optimal portfolio construction)
- Including time aspect

### Algorithms:
With a larger dataset I would have been able to test out deep learning algorithms and in-turn some potentially interesting ensemble methodologies. 

## Appendix

### Explained Algorithms:
You can find the explained algorithms in my explanatory notebook.

### Explained Markowitz Portfolio Theory
