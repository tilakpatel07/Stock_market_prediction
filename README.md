# Stock_market_prediction
redict stock prices using Stacked LSTM (Keras/TensorFlow). Trained on historical data (default AAPL). Visualizes predictions &amp; forecasts next 30 days. RMSE evaluated.


# Stock Market Prediction and Forecasting using Stacked LSTM

This project demonstrates stock market prediction and forecasting using a Stacked Long Short-Term Memory (LSTM) neural network implemented with Keras and TensorFlow 2.x. The model is trained on historical stock price data for a specified symbol (default is Apple - AAPL).

## Overview

The goal of this project is to predict future stock prices based on historical closing prices. It involves the following steps:

1.  **Data Collection:** Fetching historical stock price data using the `yfinance` library.
2.  **Data Preprocessing:** Scaling the data using Min-Max scaling to improve LSTM performance.
3.  **Data Splitting:** Dividing the data into training and testing sets.
4.  **Dataset Creation:** Creating sequences of historical data and corresponding future prices for training the LSTM.
5.  **Model Building:** Constructing a Stacked LSTM model with multiple LSTM layers and a Dense output layer.
6.  **Model Training:** Training the LSTM model on the prepared training data.
7.  **Prediction:** Using the trained model to predict stock prices on the test data and for future time steps.
8.  **Performance Evaluation:** Calculating the Root Mean Squared Error (RMSE) to assess the model's performance.
9.  **Visualization:** Plotting the actual stock prices, training predictions, and testing predictions to visually evaluate the model. Forecasting future stock prices and visualizing the trend.

## Libraries Used

* `pandas`: For data manipulation and reading.
* `pandas_datareader`: For fetching financial data (although `yfinance` is primarily used here).
* `requests`: For making HTTP requests (used by underlying libraries).
* `yfinance`: For downloading historical stock data from Yahoo Finance.
* `numpy`: For numerical operations and array manipulation.
* `matplotlib`: For creating plots and visualizations.
* `sklearn.preprocessing`: For Min-Max scaling.
* `sklearn.model_selection`: For splitting data into training and testing sets.
* `sklearn.metrics`: For calculating performance metrics like Mean Squared Error.
* `tensorflow`: For building and training the LSTM model using Keras.
* `tensorflow.keras.models`: For creating sequential models.
* `tensorflow.keras.layers`: For adding LSTM and Dense layers.

## Setup

1.  **Install the required libraries:**

    ```bash
    pip install pandas pandas-datareader requests yfinance numpy matplotlib scikit-learn tensorflow
    ```

2.  **Clone the repository (if applicable):**

    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

## Usage

1.  **Run the Python script:**

    ```bash
    python your_script_name.py
    ```

    Replace `your_script_name.py` with the actual name of your Python file containing the code.

2.  **Modify the stock symbol:**

    You can change the stock symbol to predict by modifying the `symbol` variable at the beginning of the script:

    ```python
    symbol = 'GOOGL'  # Example for Google
    ```

3.  **Adjust the time period:**

    The `period="max"` in the `df.history()` function fetches all available historical data. You can change this to a specific period (e.g., `"1y"` for one year, `"5y"` for five years).

4.  **Experiment with LSTM parameters:**

    You can modify the number of LSTM layers, the number of units in each layer, the `time_step`, the number of `epochs`, and the `batch_size` to potentially improve the model's performance.

## Code Explanation

The script performs the following main steps:

* **Data Collection:** Downloads historical closing prices for the specified stock symbol.
* **Data Preprocessing:** Scales the closing prices to a range between 0 and 1 using `MinMaxScaler`.
* **Data Splitting:** Splits the scaled data into training (65%) and testing (35%) sets.
* **Dataset Creation:** Creates sequences of `time_step` (default is 100) historical prices as input features (`X`) and the next day's price as the target variable (`y`).
* **LSTM Model Building:** Constructs a sequential LSTM model with three LSTM layers (50 units each) and a final Dense layer with one output unit for prediction. The input shape for the first LSTM layer is `(time_step, 1)`.
* **Model Compilation:** Compiles the model using the `mean_squared_error` loss function and the `adam` optimizer.
* **Model Training:** Trains the model on the training data, with validation on the test data for monitoring performance during training.
* **Prediction:** Uses the trained model to make predictions on both the training and testing data.
* **Inverse Transform:** Transforms the predictions back to the original scale using the inverse of the `MinMaxScaler`.
* **Performance Evaluation:** Calculates the RMSE between the actual and predicted prices for both the training and testing datasets.
* **Visualization:**
    * Plots the original stock prices.
    * Overlays the training predictions (shifted to align with the training data).
    * Overlays the testing predictions (shifted to align with the testing data).
    * Predicts the next 30 days of stock prices based on the last 100 days of the test data.
    * Plots the predicted future prices alongside the last 100 actual prices.

## Future Enhancements

* **Incorporate other features:** Include other relevant stock market indicators (e.g., volume, open price, high price, low price) as input features to potentially improve prediction accuracy.
* **Implement more sophisticated LSTM architectures:** Experiment with different LSTM layer configurations, dropout layers, and attention mechanisms.
* **Use different scaling techniques:** Explore other scaling methods like `StandardScaler`.
* **Implement cross-validation:** Use cross-validation techniques to get a more robust estimate of the model's performance.
* **Tune hyperparameters:** Use techniques like GridSearchCV or RandomizedSearchCV to find the optimal hyperparameters for the LSTM model.
* **Add evaluation metrics:** Include other relevant evaluation metrics like Mean Absolute Error (MAE) and R-squared.
* **Implement a more robust forecasting method:** Refine the future forecasting logic for more accurate long-term predictions.
* **Consider external factors:** Explore incorporating external factors (e.g., news sentiment, economic indicators) that might influence stock prices.

## Disclaimer

This project is for educational and demonstration purposes only. Stock market prediction is inherently complex and highly volatile. The predictions generated by this model should not be considered financial advice. Always conduct thorough research and consult with a financial professional before making any investment decisions.
