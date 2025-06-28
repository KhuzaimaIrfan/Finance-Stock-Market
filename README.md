# Finance-Stock-Market

Task 1 Stock Price Prediction and Anomaly Detection using LSTM and Isolation Forest Report 

# 1.	Dataset Preprocessing Steps

The preprocessing steps for the dataset can be summarized as follows:
•	Data Loading
The data was loaded from an Excel file containing stock market data, including columns for Date, Open, High, Low, Close*, Adj Close**, and Volume.
•	Date Conversion
The 'Date' column was converted to a datetime format to facilitate time series analysis.
•	Handling Missing Values
The dataset was inspected for missing values. Columns with missing values were handled accordingly by removing rows with NaN values.
•	Feature Engineering
Several financial indicators were created:
•	Simple Moving Average (SMA): A 20-period rolling average of the Close* price.
•	Exponential Moving Average (EMA): A 20-period weighted moving average of the Close* price.
•	Relative Strength Index (RSI): A 14-period momentum oscillator based on price changes.
•	Bollinger Bands: Upper and lower bands based on the 20-period SMA, representing volatility.
•	Anomaly Detection (Isolation Forest):
The Isolation Forest algorithm was applied to detect anomalies in the stock prices, using the Close*, SMA_20, EMA_20, and RSI_14 features. Anomalies were labeled as -1, and normal data points were labeled as 1.

# 2. Model Selection and Rationale

•	Model Selection
A Long Short-Term Memory (LSTM) neural network was chosen for predicting the stock prices. LSTM is well-suited for time series data due to its ability to capture long-term dependencies and trends. The model consists of two LSTM layers followed by a Dense layer to output the predicted stock price.
•	Rationale for LSTM
LSTM models are effective for sequential data like stock prices, as they can learn temporal patterns over long sequences of past data. The LSTM model was selected to predict future stock prices based on historical price data, along with additional features like moving averages and RSI.
•	Data Scaling
The data was scaled using MinMaxScaler to normalize the numerical features (Open, High, Low, Adj Close**, Volume, and Close*) to a range of 0 to 1. This ensures that the model works efficiently with all features on a similar scale.
•	Train-Test Split
The data was split into training and testing sets using an 80-20 split, ensuring that the model could generalize well to unseen data.

# 3. Challenges Faced and Solutions

•	Challenge 1: Missing Data Handling
The dataset had missing values, which required careful handling to avoid biased predictions. The solution was to drop rows with missing data before training the model.
•	Challenge 2: Model Overfitting
Overfitting could occur with a high number of epochs, causing the model to memorize the training data and perform poorly on test data. The solution was to set the epochs to 50, which provided a good balance between training time and model performance.
•	Challenge 3: Anomaly Detection Integration
Integrating anomaly detection with the LSTM model required careful alignment of the anomaly labels with the dataset. The solution was to apply the Isolation Forest model first and then append the anomaly labels to the original dataset.

# 4. Results with Visualizations and Interpretations

•	Model Performance
•	R-squared: 0.9957
This indicates that the model explains 99.57% of the variance in the test data. This is a very high score, meaning that the model is performing exceptionally well.
•	Mean Squared Error (MSE): 0.000202
The MSE is very low, suggesting that the model's predictions are very close to the actual values.
•	Root Mean Squared Error (RMSE): 0.0142
The RMSE is also low, confirming that the model's errors are minimal.



# •	Visualizations

Closing Price Over Time
The stock's closing price was plotted over time, showing the overall trend of the stock price.
Actual vs Predicted Values (Scaled)
A plot of the actual vs predicted stock prices, showing how well the model predicted the test data. The orange line represents the predicted values, and the blue line represents the actual values.
Actual vs Predicted Values (with Dates)
This plot shows the actual and predicted values over time, illustrating how well the LSTM model followed the trend of the stock prices over the test period.
Anomaly Detection Visualization
The plot shows the detected anomalies, represented as red points. These points are considered outliers by the Isolation Forest model.
•	Interpretation of Results:
•	The model's ability to predict the stock prices is very high, with minimal error in the predictions.
•	The R-squared score indicates that the model is highly effective in explaining the variance in the data.
•	The anomaly detection results are also helpful in identifying outlier data points that could represent unusual market behavior or events.
