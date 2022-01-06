### **Project Name**  
Forecasting the amount of licenses given to new businesses in the city of Chicago 

## **The Goal**
the Department of Business Affairs and Consumer Protection in the City of Chicago issuing licenses to businesses. In this project we want to fit a model for future projections of licenses issuing for better strategic preparations in advance. During 2020, due to a coronavirus outbarke, the economic activity significantly damaged, it was clearly seen in the data.this drastic changes makes the prediction more complicated and challenging. I added external data as features to help the models with prediction. Using the collected data I fitted 5 different ML algorithms and 1 DL algorithm to predict the amount of licenses given.  

## **Data Origin**
This project is based on data from two sources:  
  1. Chicago Data Portal  
  2. FRED Economic Data  
 
**Note:** links for the relevant data in the appendices chapter  

## **Data Description**
The final dataset that was used for training ML and DL algorithms contains 140 observations with monthly data from Jan 2010 to Aug 2021. All the variables were transformed using log function.  
Variables:  
'Month' - month  
'Log_Count_License' - log of issued licenses during the month (app. 1)  
'Log_Sum_Incentive' - log of incentive amount approved during the month (app. 2)  
'Log_HPI' - log of S&P/Case-Shiller IL-Chicago Home Price Index  (CHXRSA) (app 3.)  
'Log_UnEmp' - Unemployment Rate in Chicago-Naperville-Elgin, IL-IN-WI (MSA) (CHIC917URN) (app. 4)  
'Log_Elec' - log of Average Price: Electricity per Kilowatt-Hour in Chicago-Naperville-Elgin, IL-IN-WI (CBSA) (APUS23A72610) (app. 5)  

**Note:** I added to the database a 3 months and 6 months lagged independent variables (features)

## **Analysis Description**
**Step 1** – preprocessing: calculate monthly aggregates (only where needed), combine all data collected, Transform to log’s, Add lagged feature variables.  
**Step 2** – data exploration: correlation matrix, licenses time series composition extraction, linear regression for variables dependencies exploration.  
**Step 3** – fitting 5 different scikit learn ML classification algorithms:  
  1. Linear Regression (LR)
  2. Random Forest Regressor (RFR)
  3. XGB Regressor  (XGB)
  4. Seasonal Auto-Regressive Integrated Moving Average with eXogenous factors (SARIMAX)
  5. Support Vector Regressor (SVM)

**Step 4** - fit PyTorch LSTM model  
**Step 5** - comparing the prediction results using common metrics and graphical representation

## **Results**
XGB was the most efficient predicting model with the lowest mean absolute and squared error. The LSTM model is the second most efficient. Surprisingly, the SARIMAX model was the last in the list with the worst performance. Together with the linear regression the prediction of the SARIMAX model was highly impacted from the incentives variable which were approved only three month between Aug 2020 and Aug 2021.

## **Discussion**
The following approaches could be taken to improve the forecasting:
There are techniques to find the most appropriate AR and MA parameters for the ARIMA model. With some configuration of the SARIMAX model parameters the results can be improved
The features can be weighted such that the models would be more balanced and had less impact from from drastic changes in one of the features

## **KeyWords**
Forecasting, Prediction, Business licenses, small business incentives, Linear Regression, Random Forest Regressor, XGB Regressor, SARIMAX, Support Vector Regressor, LSTM, PyTorch

## **Appendices**
1. https://data.cityofchicago.org/browse?q=licenses&sortBy=relevance  
2. https://data.cityofchicago.org/Community-Economic-Development/Financial-Incentive-Projects-Small-Business-Improv/etqr-sz5x  
3. https://fred.stlouisfed.org/series/CHXRSA  
4. https://fred.stlouisfed.org/series/CHIC917URN  
5. https://fred.stlouisfed.org/series/APUS23A72610
