# Dispersion-Stratergy-on-Indian-Market-Stocks

### Strategy motivation 
We calculate the volatility of the index and its constituent stocks at a suitable intraday frequency.

Once we have the volatility for each stock component and Index, we will calculate the correlation between the volatility of the index and weighted (weights explaining the index spot price) average of that of the constituent stocks as well.



### Dispersion Statergy 
We calculate the average implied volatility of stocks and index using the first OTM strike price contracts with the following formula.

Average IV = {(IV of Put * Distance of stock price from the strike price of the 1st OTM Call) + ((IV of Call * Distance of stock price from the strike price of the 1st OTM Put)}/ (Distance between strikes).

Then we calculate the weighted average of the average IV of stocks by their weights on the index and calculate the ratio - IV of BANKNIFTY/ weighted average IV of the stocks.

This ratio is also called dirty correlation and is calculated for every 15 minutes. Based on this we calculate a moving Z score on a look-back period of 30.

If the Z score is greater than 1 we expect the BANKNIFTY IV to come down or the weighted average IV of the stocks to go up and hence, we short first OTM Strangle of BANKNIFTY and buy first OTM strangle of all stocks. The contrary is for Z score less than -1.

After we enter as per above rules, at every 15 minutes we hedge the deltas - we calculate the delta of all our positions and bring it to close to zero.

It may be done by calculating the delta of each stock and index in our portfolio and if the this delta per quantity for each stock is greater than 0.1 or less than -0.1 we hedge it appropriately by taking positions in the futures.

If the Z score reaches a magnitude less than 0.8 we square of all the positions and calculate the PnL.
