# Training-Models-for-Making-Walmart-s-Sales-Predictions
Our group aimed to develop an accurate and scalable forecasting solution to help Walmart predict daily sales amounts at the item level by machine learning.

The dataset is from Kaggle: https://www.kaggle.com/competitions/m5-forecasting-accuracy/data
The data covers all stores in three US states and includes item level, department, product category and store details. In addition, it has explanatory variables such as price, promotions, day of the week, and special events which are helpful to make predictions to each sales value of products of specific days. The dataset calender contains information about the date on which the product was sold. Also, it records the day of the week, month, and year for each of the 1969 days. And its sell_price.csv contains information about the price of each products sold in each store and date. 

In the LSTM model training code, the sales of the current day are highly correlated with the sales of the previous 14 days. Therefore, we choose these days to look back in the data. In the config, the epochs are 10, the batch_size is 128, the neuron unit is 64, the activation function is RELU. We also transformed some variables using one-hot-encoding, because there’re some non-linear variables. 

We train the prediction model for 10 random unique products. Taking a training process as an example. In the final epoch, the training loss and validation loss have dropped to around 1, and the RMSE is 3. So, the training accuracy and the config for training seems to be satisfactory for predicting.

The results are 8 prediction graphs based on each trained model. We can find that the RMSE values are acceptable, but some predictions are completely different from the true future. I think this is because although a unique product’s number of sold is put together to train the model, it’s hard to predict the sales number in a single store.
