# HUFEUR_TA 
Project deatails:
Started: 2024.06.10
Current status: In Progress
Expected finishing date: 2024.07.31

The aim of this project is to create a code which can do Trend Analysis on various FX Rate pairs by focusing on the **weekly** japanese candlestick patterns and in general, the price movements of a pair. 
The sole purpose of this is to provide a differentiation for my VAR analysis on the same dependent variable which is the HUF/EUR.

What we need before start coding?

**1) DATA COLLECTION**
<br> Database of FX Rates in weekly time period from 2006.01.01 until 2023.06.31
**The following pairs are needed : <br>HUF/USD	<br>CZK/USD	<br>PLN/USD	<br>DKK/USD	<br>SEK/USD	<br>CHF/USD	<br>EUR/USD**  . <br>These are the currencies of EU member states that are of course not within the Eurozone.
For this purpose i will use the YFINANCE library, that is pretty good for this i assume
  
**2) DECIDING ANALYTICAL METHODS;   INDICATORS&PATTERNS**
We need the following **indicators:**
I can use: Pandas_Ta and Ta-Lib for the below mentioned indicators.
<br>**Moving Averages (SMA, EMA):** Identify trends and potential reversal points.
<br>**MACD:** Signal changes in the strength, direction, momentum, and duration of a trend.
<br>**RSI:** Identify overbought or oversold conditions.
<br>**Bollinger Bands:** Show volatility and potential reversal points.
<br>**ATR:** Measure volatility.
<br>**OBV:** Use volume to predict price changes.

Fibonacci Retracement must have to be calculated manually :( I think i will create some sort of reusable code for this one
<br>**Fibonacci Retracement:** Identify potential support and resistance levels.

**Japanese candlestick patterns:**
Here also we can use the Pandas_ta or Ta-lib
<br>** Two Crows **
<br>** Three Black Crows**
<br>** Three Inside Up/Down**
<br>** Three Line Strike       **
<br>** Three Outside Up/Down        **
<br>** Three Stars In The South        **
<br>** Three Advancing White Soldiers        **
<br>** Abandoned Baby        **
<br>** Advance Block        **
<br>** Belt hold       **
<br>** Breakaway        **
<br>** Closing Marubozu        **
<br>** Concealing Baby Swallow        **
<br>** Counterattack        **
<br>** Dark Cloud Cover        **
<br>** Doji        **
<br>** Doji Star        **
<br>** Dragonfly Doji        **
<br>** Engulfing Pattern        **
<br>** Evening Doji Star        **
<br>** Evening Star        **
<br>** Up/Down gap side by side white lines     **
<br>** Gravestone Doji        **
<br>** Hammer        **
<br>** Hanging Man        **
<br>** Harami Pattern        **
<br>** Harami Cross Pattern        **
<br>** High Wave Candle       **
<br>** Hikkake Pattern        **
<br>** Modified Hikkake Pattern        **
<br>** Homing Pigeon        **
<br>** Identical Three Crows        **
<br>** In Neck Pattern       **
<br>** Inverted Hammer        **
<br>** Kicking        **
<br>** Kicking   bull/bear determined by the longer marubozu       **
<br>** Ladder Bottom        **
<br>** Long Legged Doji        **
<br>** Long Line Candle        **
<br>** Marubozu        **
<br>** Matching Low        **
<br>** Mat Hold        **
<br>** Morning Doji Star        **
<br>** Morning Star        **
<br>** On Neck Pattern       **
<br>** Piercing Pattern        **
<br>** Rickshaw Man        **
<br>** Rising/Falling Three Methods        **
<br>** Separating Lines        **
<br>** Shooting Star        **
<br>** Short Line Candle        **
<br>** Spinning Top        **
<br>** Stalled Pattern        **
<br>** Stick Sandwich        **
<br>** Takuri (Dragonfly Doji with very long lower shadow)        **
<br>** Tasuki Gap        **
<br>** Thrusting Pattern        **
<br>** Tristar Pattern        **
<br>** Unique 3 River        **
<br>** Upside Gap Two Crows        **
<br>** Upside/Downside Gap Three Methods        **




**3) METHODOLOGY**

So I have to go through the chart with the weekly candles and identify when does these patterns occour and create a different alert for all occurence. Basically, each indicator and pattern if appear, by theory it should predict the price movement of the observed ticker.  Trend analysis is good also for a past analytics and also for forecasting, but economically it is out of question utterly useless to predict only by price.
We need to use some pre-built libraries for this progress to make it easier to find patterns and indicator signs.
The followign libraries are needed at first thought:
-Pandas
-Pandas_ta
-TA_lib
-MPLfinance (coloring individual candlesticks to highlight various patterns
-yfinance 

**4) How i imagine the code should go (note for myself)**
So the first target will be the HUF/EUR chart, not to complicate with other at first glance. I imagine the following:
We create a table where there are 3 column. The first column will contain the name of the indicator or the pattern, the second column will show the number of occurence of the pattern or number of occurence of a bullish/bearish indicator. The third column should show the number of predicted movements became true. ALso now i think about i will definetiley need to store each and every occurence, to be able to visualise it and highlight when does that actually happened. THe question is how?

I want something like this as a output and as a unique table from which i will do the further elaboration:

| Type          | signal        | Name                | Occurence     |
| ------------- | ------------- | -------------       | ------------- |
| Indicator     | Bullish       | HAMMER              | 2022.01.02    |
| Pattern       | Bearish       | Bollinger Bands     | 2017.01.02    |

Example:
1) going through the chart and look for a Bullish  Hammer candle, if find 1,  save it somewhere to a  dictionary and go further and check if there exists more or not. If the for loop is done, went through all the candles and find x amount of bullish hammers which all added to the previously mentioned table



I also would like to create a closeness variable but with considering the candlesticks and volume also, not the fx rate on its own.
