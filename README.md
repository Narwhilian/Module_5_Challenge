# Financial Planner

This application takes in real time data for cryptocurrency prices as well as close prices for both AGG and SPY to analyze a clients portfolio exposure to cryptocurrency, bonds, and stocks respectively. It evaluates the users portfolio to see if it has sufficient funds for emergencies as well as forecasts stock and bond portfolio performance over both a 30 year and 10 year period utilizing the python MCForecast tools module.

---

## Technologies

This project uses the Python Programming language in a Jupyter Notebook as well as the following libraries
    
    - os
    - requests
    - json
    - pandas
    - dotenv
    - alpaca_trade_api
    - MCForecast Tools


---

## Installation Guide

To install you will want to pull the entire Financial_Plan folder from github including its subfolder
    
    * Subfolder
        * Images (data folder)
        * MCForecastTools.py (Monte Carlo forecasting python import
        * financial_planning_tools.ipynb (the jupyter notebook itseld)
        * ReadMe (This file)


---

## How it works

1) First the user will open the financial_planning_tools.ipynb notebook in the Financial_Plan folder
2) The user will have to also ensure that they have a .env file containing an alpaca api key and an alpaca secret key labled as ALPACA_API_KEY and ALPACA_SECRET_KEY respectively
3) Then the user will simply run each cell in the notebook to get its output

    i) The app will establish the number of BTC and ETH in the users crypto wallet as well as the users monthly income in USD (preset as 12000)
    
    ii) Then it will establish the url access for BTC and ETH prices, making a call for each and storing them each as their own json
    
        - it will then extract the current BTC and ETH prices from their json files
        - it will then multiply the current crypto prices with the respective number of coins in the wallet to generate the USD value of each
        - finally it will combine the values of BTC and ETH to calculate the total value currently held in the users crypto wallet
    
    iii) Then it will establish the number of SPY and AGG shares in the users stock/bond portfolio
    
    iv) Then it will call both the alpaca api key and the alpaca secret key from the .env file and establish the representational state transfer (REST) for the alpaca API
    
    v) Then it will use the list of tickers, timeframe, and start/end dates to call the alpaca API for the most recent (2020-08-07 in this case) prices of AGG and SPY
    
        - It will then extract the close price for both SPY and AGG from the DataFrame and use that to calculate the price of each investment
        - Then it will combine the two investments to calculate the total current value of the stock and bond portfolio
    
    vi) Then it will evaluate the emergency fund using all of the above data to
        
        - Vizualize the users crypto wallet and stock/bond portfolio as a pie chart
        - Check if the total savings is greater than the ammount reccomended for the emergency fund (3x monthly income) and display a message alerting the user of their status
    
    vii) Then it will create a financial planner for retirement by
        
        - establishing various portfolio weights
        - using the alpaca api to call historical price data for the last 10 years
        - calculating a monte carlo forecast using the MCForecastingTool.py for both a 30 year time period as well as a 10 year time period
        - plot the 500 different forecasts like below 
    ![5-4-monte-carlo-line-plot](https://user-images.githubusercontent.com/84096312/124307488-bfe5ae80-db1c-11eb-8a9f-378023c1e625.png)
        - plot the distribution of returns like below
    ![5-4-monte-carlo-histogram](https://user-images.githubusercontent.com/84096312/124307542-d25fe800-db1c-11eb-82a8-143605c5a064.png)
        - And finally calculate a 95% confidence interval of the users stock/bond portfolio for a 30 year investment as well as a 10 year investment


---

## Usage

Overall it should be a very simple application to use, all you need to do is open the financial_planning_tools.ipynb app in the Financial_Plan folder and run each cell in order

**It is crucial that the user has a .env file containing both an alpaca api key and an alpaca secret key labled like below with the users keys in place of (Your Key here)**

    ALPACA_API_KEY = "<Your Key here>"
    ALPACA_SECRET_KEY = "<Your Key here>"


---

## Contributors

Colin Benjamin

Linkedin: [Colin Benjamin](https://www.linkedin.com/in/colinbenjamin/)
    
email: cbenjamin33@gmail.com

---

## License

MIT
