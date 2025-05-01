# FinalProject
 *Statistical Arbitrage* ~~ Mean-Reverting Algorithm


# Main goal for this project

The main idea of this project is to succesfully code, deploy and backtest a *Mean-Reverting* algorithm. This algorithm, with help of some external neural networks and deep learning models will trade the reversion into the mean of two pairs, in this case NIKKEI and VIX.

## Models used in the project

There will be a few machine learning and deep learning models implemented, to make sure we minimise our losses when trading:

- *OLS* model: This model will be used to create the fair *Spread* This spread will be the main time-serie traded by the algorithm.
  
- *ARIMA* model: The VAR model will be used to predict the *Spread*. Why I selected a VAR model is because I want the model to have in mind the relationships between the two asstes. What this VAR model allows me is to see how much of a change in one asset will impact the other.
  
- *FINBERT* model: FINBERT is a natural processing model that ranks by sentiment the different news and headlines.


## Reasoning behind the trades of this project 

The reasoning of the trades taken by this algorithm will be the following:

**IF** the price of the *Spread* is **above or below** a barrier (depending on which one; Upper or Lowers ):

We check the prediction of the **VAR** model at **Xt** for the price at **X(t+1)**

**IF** the prediction of the **VAR** model is **Lower or higher** than the actual price at **Xt** (depending on which barrier it crossed) 

We can then know that the price prediction of the model indicates there is going to be a reversion into the mean, allowing us identify a trade.

**LASTLY** we check for the prediction of the **LSTM NN** 

**IF** the prediction of the **LSTMnn** is long on the Nikkei and short on the VIX or viceversa (depending on which barrier it crossed)

This can then tell us that all the models indicate that the price of the *Spread**  will revert to the mean:

**GIVING US A TRADE**

In terms of the exits:

Only when a trade is entered we can exit it by the price of the *Spread* **Touching the mean** or by **Touching our stoploss**.

The **The stoploss will be calculated with the standard diviations**.
            
