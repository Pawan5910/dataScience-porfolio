# Cryptocurrency Price Forecasting and Prediction using ARIMA, SARIMAX and LSTM

## Abstract
Cryptocurrency, a virtual type of currency, is a hot topic in today’s world, which is gaining a lot of attention and is attracting many new investors and traders every day. This gaining popularity has made the concept of cryptocurrency price prediction to be a part of a lot of studies. This project compares the Auto Regressive Integrated Moving Average (ARIMA), Seasonal Auto Regressive Integrated Moving Average eXogenous SARIMAX, and the Long Short-Term Memory (LSTM) models, to find the best model for the Cryptocurrency Price forecasting and prediction. The cryptocurrency used in this project is Bitcoin, and all the trading data is collected for the same. This project also involves Sentiment analysis, as the sentiment scores of the tweets related to Bitcoin are also considered as a feature while training these models, thus considering the human aspects as a factor for prediction. The results proved that ARIMA and SARIMAX models gave the best accuracy when the entire data set is trained rather than the smaller datasets of two halves. Also, SARIMAX had the best accuracy for the short-term prediction (day 1), and as the number of days increased, the accuracy gradually decreased. The LSTM model gave the best accuracy after implementing the feature selection using the SelectKbest and Principal Component Analysis (PCA) Methods. On comparing the models, it was inferred that SARIMAX with the Mean Squared Error (MSE) of 0.00027 is the most optimal model for price prediction and forecasting, with LSTM model having the second least accuracy of 0.0008 and the ARIMA model having the biggest MSE of 0.003.

## Dataset
**Trading Data**:

The trading data is the set of features collected in the form of time series, which includes a lot of attributes which defines and affects the cryptocurrency market. For this project, only Bitcoin, which is a type of cryptocurrency, is considered. This data for Bitcoin is collected using the Yfinance API:
Yfinance API:  The Yahoo finance API, also known as the Yfinance API is the collection methods and libraries used to obtain data about financial markets like stocks and cryptocurrency. The data can be real time, or it can be collected over a long period of time. This API also offers information about the regular currencies, market news, market analysis and many more. This API is very popular because of its simplicity. The setup of this API is quick and the range of the data that it offers is adequate and large. 
The bitcoin data that is collected consists of the following attributes:
- Timestamp: Gives the starting time of the datapoint collected. The timestamp is obtained in the UNIX format.
- Open: Gives the opening price of the bitcoin for that day in a minute’s interval.
- High: Gives the highest price of the bitcoin that it attains that day, in a minute’s interval
- Low: Gives the lowest price of the bitcoin that it drops to that day, in a minute’s interval
- Close: Gives the closing price of the bitcoin, in a minute’s interval.
- Volume_BTC: Gives the volume of the transactions that is undertaken for bitcoin.
All these features are collected in the US dollars. 

The data is collected from the date 2018-01-01 to the date 2022-08-19, which comprises of 1692 records. The code for scarping the bitcoin data could be found [here](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Code/Scraping_Yahoo.ipynb).

**Social Media / Twitter Data**

Many studies have proven that integration of the social media data, as a feature pertaining to human / public sentiment can have a huge impact on stock or cryptocurrency price prediction. For this project, the social media platform that is chosen is Twitter. It is one of the most popular microblogging sites where massive number of instant messages, which can be thoughts or opinions known as tweets are posted daily. The topics or domain of interest for these tweets are not limited, as a user can post his/her views about any current issues, marketing topics, entertainment, sports, music, and many more with the help hashtags (#). Hence this data can be used for the analysis of cryptocurrency market trends as we can have the views of different people, who are actively involved in the cryptocurrency market. 
The tweets related to bitcoin are collected using the Snscrape API in this project:
- Snscrape: It is a tool exclusively used for scraping content from the Social Networking Sites (SNS). The features that can be scraped are user ids, tweets, hashtags, posts and many more. This does not require the usage of Twitter’s API. Snscrape can also collect data from other social networking websites like Facebook, Instagram, Reddit and many more. And, legally Twitter has no restrictions on users scraping the data from the site, hence it is popular amongst the data analysis and sentiment analysis research. Snscrape is better than other scraping APIs like Tweepy, as Tweepy has a scraping limit of just 3200 tweets, and the tweets available can only be a week old to the furthest. Snscrape has no limit on the number of tweets that can be scraped or the time window that must be set. 
The tweets retrieved from sncrape are obtained using the keyword ‘Bitcoin’, The tweets were collected from the date 2018-01-01 to 2022-08-19, where over 250k tweets were collected, with a limit of 150 tweets per day. The attributes that were collected are Timestamp, Tweet Id, and the Tweet. Data cleaning was done on the tweets as the hashtags, URLs and blank spaces were removed from the tweets. The data cleaning process was done using the pythons ‘re’ module, which is used for regular expressions. The code to scrape the  tweets related to bitcoin of a particular day could be found [here](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Code/snscrape.ipynb).

All the datasets could be found [here](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Dataset.7z).

## Approach

- The crytocurrency price forecasting was done using [ARIMA and SARIMAX](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Code/Arima_Sarimax.ipynb) as a first approach. The data is checked for stationarity by using the ADF and KPSS tests, and differencing is implemented on the data to make the data stationary. The data is checked for seasonality, and as the seasonality component was found in the data, the data was found to be suitable for the SARIMAX implementation. The Order for ARIMA and the Seasonal Order for SARIMAX is found using the ACF and the PACF graphs. The data is normalized, and three kinds of experiments were conducted on both the models, where the entire data, first half and the second half of the data were used for the training of these models. It was found that both the models gave the best accuracy when it was trained with the entire dataset, as this gives the model to understand and analyze both the lower and higher trends of the data fed and make the forecasting and prediction more accurate. For the comparison purpose, only the results of the model obtained for the entire data is considered, and SARIMAX proved to be a better model with a MSE of 0.00027 as compared to the MSE of 0.003 of ARIMA. During the prediction of SARIMAX it was also noticed that SARIMAX has the better accuracy for short term predictions, and the accuracy gradually drops, as the days of the prediction increases.
- The [sentiment analysis](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Code/Hugging__face.ipynb) for the scrapped tweets related to bitcoin is conducted, to include the sentiment analysis score as an additional feature for forecasting.
- The cryptocurrency forecasting a is conducted using LSTMs as an alternate approach. The notebook could be found [here](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Code/LSTM.ipynb).
- Feature selection was conducted using Principle Component Analysis (PCA) and selectKbest and the LSTM model is trained using the selected features. The code could be found [here](https://github.com/Pawan5910/dataScience-porfolio/blob/main/Bitcoin%20price%20prediction%20and%20analysis/Code/LSTM_featureSelection.ipynb).
- For the implementation of LSTM, the sliding window technique is utilised. The data is normalised and initially only the close values are fed to the sliding window method, to produce 5 input features. The model with the learning rate of 0.0001, 300 epochs and 3 dropout layers to avoid overfitting, gave an MSE of 0.002. This score of MSE improved when the sliding window method was applied to all the features, resulting in 35 input features, and the model gave a MSE of 0.001. Feature scaling methods like SelectKbest and PCA was applied on the data, to selelct the best features only, after which the number of features dropped from 35 to 27. This model achieved the best accuracy for LSTM with the MSE of 0.0008

## Conclusion

Even though LSTM outperformed ARIMA, it had a higher MSE than SARIMAX. Hence in this project we can conclude that SARIMAX provides the best forecasting and prediction for the Cryptocurrency price, with LSTM to be a very close second as the MSE is very close to that of SARIMAX.

