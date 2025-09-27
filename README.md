# Training-Models-for-Making-Walmart-s-Sales-Predictions
Our project is designed to assist Walmart with accurate daily sales forecasting. 
Our goal is to create models to predict the sales of individual items over the next 28 days.



The dataset is from Kaggle: https://www.kaggle.com/competitions/m5-forecasting-accuracy/data
The data covers all stores in three US states and includes item level, department, product category and store details. In addition, it has explanatory variables such as price, promotions, day of the week, and special events which are helpful to make predictions to each sales value of products of specific days. The dataset calender contains information about the date on which the product was sold. Also, it records the day of the week, month, and year for each of the 1969 days. And its sell_price.csv contains information about the price of each products sold in each store and date. 

The dataset includes four csv files. What we do first was combining all the files together to a single csv file, which reach to 58 million rows.However, we found that the csv file is too large to run, so before deep learning, we split the data into three parts based on their product category. And we continue to split them into training, validation and testing dataset. We also fill the empty cells and turn all the non-numerical values to numbers for LSTM model training. We use LSTM model because this dataset is time series.

Firstly, household.csv was used to extract the top200 products with the highest sales volume, and then OneHotEncoder was used for data pre-processing. Linear, random forest and XGBoost regression models were used for data processing. According to the analysis results, the XGboost model has the smallest MSE and the largest R2, so it has the best performance. Finally, the paper also analyzes the importance of features, and simply judges the features that are helpful to sales.

In the LSTM model training code, the sales of the current day are highly correlated with the sales of the previous 14 days. Therefore, we choose these days to look back in the data. In the config, the epochs are 10, the batch_size is 128, the neuron unit is 64, the activation function is RELU. We also transformed some variables using one-hot-encoding, because there’re some non-linear variables. 

We train the prediction model for 10 random unique products. Taking a training process as an example. In the final epoch, the training loss and validation loss have dropped to around 1, and the RMSE is 3. So, the training accuracy and the config for training seems to be satisfactory for predicting.

The results are 8 prediction graphs based on each trained model. We can find that the RMSE values are acceptable, but some predictions are completely different from the true future. I think this is because although a unique product’s number of sold is put together to train the model, it’s hard to predict the sales number in a single store.
