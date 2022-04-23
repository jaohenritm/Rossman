# Rossman Sales Forecast

![alt text](https://github.com/jaohenritm/Rossman/blob/main/img/63b806b1494a7fbd9cb05271667b9c61.png)

# 1. Rossmann Business
Rossmann is one of Europe's largest drugstore chains. With around 56,200 employees and over 4,000 stores. In 2019, Rossmann had sales of over €10 billion with majority of that sales on Germany. With such a large number and variety of stores, it is very important that the management of the company have a base of sales in the future, with this a business issue has arisen that the company's CFO needs to resolve at the moment.

## 1.1 Problem Context
The Rossmann CFO needs to do some renovations on their stores and requested for all managers to give him some kind of sales forecast for the next 6 weeks. With that forecast he will know how much he will be allowed to invest in that renevues. As the managers don't have the tools needed to do that forecast, they asked the Data Team to develop a solution for their business problem.

# 2. Data
***Observation: This solution is fictious and was developed with open data that was made avaiable through the Kaggle platform.***

***Link: https://www.kaggle.com/c/rossmann-store-sales/data***


Most of the fields are self-explanatory. The following are descriptions for those that aren't.

- ***Id*** - an Id that represents a (Store, Date) duple within the test set
- ***Store*** - a unique Id for each store
- ***Sales*** - the turnover for any given day (this is what you are predicting)
- ***Customers*** - the number of customers on a given day
- ***Open*** - an indicator for whether the store was open: 0 = closed, 1 = open
- ***StateHoliday*** - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None
- ***SchoolHoliday*** - indicates if the (Store, Date) was affected by the closure of public schools
- ***StoreType*** - differentiates between 4 different store models: a, b, c, d
- ***Assortment*** - describes an assortment level: a = basic, b = extra, c = extended
- ***CompetitionDistance*** - distance in meters to the nearest competitor store
- ***CompetitionOpenSince[Month/Year]*** - gives the approximate year and month of the time the nearest competitor was opened
- ***Promo*** - indicates whether a store is running a promo on that day
- ***Promo2*** - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating
- ***Promo2Since[Year/Week]*** - describes the year and calendar week when the store started participating in Promo2
- ***PromoInterval*** - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store

## 2.1 Planning the Solution
After collecting the Data, the next step was to do a really deep Exploratory Data Analysis (EDA) to validate some hypothesis to see how the data behaves and how every feature affects the amount of sales.

## 2.2 Outstanding Hypothesis
We checked at total 12 hypothesis to see if the data behaves like it was expected, in fact the majority of the hypothesis seems to be false. We selected some that we think are the most important amongst them.


**H8: Stores should sell more over the years**

**Result: False. The stores sales are dropping 5% each year.**
![alt_text](https://github.com/jaohenritm/Rossman/blob/main/img/H8.png)

**H9: Stores should sell more in the second semester**

**Result: False. The stores sells 15% less in the second semester when compared to first semester.**
![alt_text](https://github.com/jaohenritm/Rossman/blob/main/img/H9.png)

**H10: Stores should sell more after the day 10 of the month**

**Result: Truth. The stores have nearly the double of sales after day 10. (In total, not average)**
![alt_text](https://github.com/jaohenritm/Rossman/blob/main/img/H10.png)

**H11: Stores should sell less in the weekend.**

**Result: Truth. The stores sells much less during the weekend, especially during sundays.**
![alt_text](https://github.com/jaohenritm/Rossman/blob/main/img/H11.png)

## 2.3 Overview of all Hypothesis
| **Hypothesis** | **Result** | **Final Result** |
| --- | --- | --- |
| H1: Stores with more sortment should sell more. | False | Stores with more sortment sell less. | 
| H2: Stores with nearly competitors should sell less. | False  | Store with nearly competitors sell more. | 
| H3: Stores with nearly long term competitors should sell more.| False  | Stores with recent competitors sell more. | 
| H4: Stores with active promotions for a longer time should sell more.| False | Stores with longer promotions sell less after a certain time. | 
| H5: <s>Stores with more days of promotion should sell more.</s> | Not Verified | |
| H6: Stores with consecutive promotions should sell more.| False  | Stores with consecutive promotions sell less. |
| H7: Stores open during Christmas should sell more.| False  | Stores open during Christmas sell less. |
| H8: Stores should sell more over the years. | False | The stores sales are dropping 5% each year. |
| H9: Stores should sell more in the second semester. | False | The stores sells 15% less in the second semester when compared to first semester. |
| H10: Stores should sell more after the day 10 of the month. | True | The stores have nearly the double of sales after day 10. (In total, not average) |
| H11: Stores should sell less in the weekend. | True | The stores sells much less during the weekend, especially during sundays. |
| H12: Stores should more during school holidays.| False  | Store sell less during school holidays with exception on July and August. |


## 2.4 The Selection of Features
As we did the EDA, it was perceived that some features in this dataset are impossible for now to be used in this project like.
- Just used days where the Store was with OPEN status and have more sales than 0.
- Customers can't be used as we don't have the number of how many customers the store will have.
- Used Boruta algorith to help with the feature selection.

# 3. Forecast Model
At total we tested 5 models which were: 
- Average (Used as baseline)
- Linear Regression
- Linear Regression Regularized
- Random Forest Regressor
- XGBoost Regressor.

We used a average model to use as baseline for comparison with the other models that will be tested. The second step was to use some linear models as the Linear and lasso, but the result achieved with theses 2 was not a good one, so we parted to use non-linear models like Random Forest Regressor and XGBoost Regressor.

## 3.1 Model Performance
The model that achieved the best performance was the XGBoost amongst all of them, so we proceeded with him and started to do the fine tuning. After that we tested the model one more time and achieved even better results. The metrics used were ***MAE, MAPE and RMSE***

- MAE (Mean Absolute Error) - Shows the absolute mean error of the model.
- MAPE (Mean Absolute percentage error) - It represents the MAE in percentage.
- RMSE (Root Mean Squared Error) - Represents the mean absolute error squared, it's nearly the same as MAE but it is more sensible about the outliers.

<p align="center">
  <img 
    width="342"
    height="59"
    src="https://github.com/jaohenritm/Rossman/blob/main/img/xgboost-result.png"
  >
</p>



## 3.2 Business Performance
The spreadsheet below shows the results obtained with the model with a sample of stores of the dataset. Also is shown the worst and best scenarios for the store using the MAE metric, with that the CFO should have a notion about how much the stores should sell in future.

<p align="center">
  <img 
    width="494"
    height="160"
    src="https://github.com/jaohenritm/Rossman/blob/main/img/scenarios.png"
  >
</p>

With that we also did some forecast about the total amount of sales that the Rossmann stores would do. Using our margin of error the difference between the best and the worst scenario is R$1.707.773 that should be analyzed by the CFO if it's satisfactory or not.

<p align="center">
  <img 
    width="234"
    height="108"
    src="https://github.com/jaohenritm/Rossman/blob/main/img/final_result.png"
  >
</p>


# 4 Deploy
We created a Telegram Bot to responds everyone that wants to check a certain store on our project. To do that you just need to open a conversation with the RossmannBot and tell the number of the store that you want to see the forecast. If the Store ID doesn't exist, he will return a message saying that you can't consult this store and inform another number. Informing a correct Store ID number he will tell the forecast of the store for the next 6 weeks.

- The API with the Forecast Model was hosted in the Heroku and can be consulted in this URL: https://prediction-sales-rossmann.herokuapp.com/
- Telegram Bot: https://t.me/RossSalesBot

<p align="center">
  <img 
    width="284"
    height="580"
    src="https://github.com/jaohenritm/Rossman/blob/main/img/telegram-bot.png"
  >
</p>

# 5 Conclusion
The result was a satisfactory one for the business problem as the prediction model have a relative small error and with that result the CFO can group with the business team and do the planning of the revenues that he was intending to do in the beginning of the project. 


Still things to do in the next CRISP cycle:
- Verify the fifth hypothesis.
- Try to develop a forecast of how many customers the store will have to use customers on the forecast sales model.
- Check why some stores don't have results (If they were shutdown or it's a bug).
- Test other models and do other fine tunings.
