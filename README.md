# Rossman Sales Forecast

# 1. Rossmann Business
Rossmann is one of Europe's largest drugstore chains. With around 56,200 employees and over 4,000 stores. In 2019, Rossmann had sales of over €10 billion with majority of that sales on Germany. With such a large number and variety of stores, it is very important that the management of the company have a base of sales in the future, with this a business issue has arisen that the company's CFO needs to resolve at the moment.

## 1.1 Problem Context
The Rossmann CFO needs to do some renovations on their stores and requested for all managers to give him some kind of sales forecast for the next 6 weeks. With that forecast he will know how much he will be allowed to invest in that renevues. As the managers don't have the tools needed to do that forecast, they asked the Data Team to develop a solution for their business problem.

# 2. Data
***Observation: This solution is fictious and was developed with open data that was made avaiable through the Kaggle Platform in the link: https://www.kaggle.com/c/rossmann-store-sales/data***


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


