# FinalProject
 *Statistical Arbitrage* ~~ Mean-Reverting Algorithm


# Main goal for this project

The main idea of this project is to succesfully code, deploy and backtest a *Mean-Reverting* algorithm. This algorithm, with help of some external neural networks and deep learning models will trade the reversion into the mean of two pairs, in this case NIKKEI and VIX.

## Models used in the project

There will be a few machine learning and deep learning models implemented, to make sure I minimise my losses when trading:

- *OLS* model: This model will be used to calculate the fair *Spread* This spread will be the main time-serie traded by the algorithm.
  
- *ARIMA* model: The ARIMA model will be used to predict the *Spread*. Why I selected a ARIMA model is due to the time-seire being univariate and its ability to caputre complex patterns in such data. What this ARIMA model allows me is to predict the value of the spread after crossing one of the thresholds and with this minimize my exposure to false signals.
  
- *FINBERT* model: FINBERT is a natural processing model that ranks by sentiment the different news and headlines. This model will be used in my algorithm to define and dinamically adjust the barriers for the mean-reversion.


## Reasoning behind the trades  

The reasoning of the trades taken by this algorithm will be the following:

Firstly, the thresholds will be defined by the **FINBERT** model depending on the *sentiment* score for that day,

**IF** the price of the *Spread* is **above or below** a barrier (depending on which one: Upper or Lower ):

We check the prediction of the **ARIMA** model at **Xt** for the price at **X(t+1)**

**IF** the prediction of the **ARIMA** model is **Lower or higher** than the actual price at **Xt** (depending on which barrier it crossed) 

We can then know that the price prediction of the model indicates there is going to be a reversion into the mean, allowing us identify a trade.


**GIVING US A TRADE**

In terms of the exits:

The only way to exit a trade is with the *Spread* **reverting to the equilibrium**.

When a trade is in place, the model wont check for more entries. Only when the trade is exited the model will check for new possibilities.
            
