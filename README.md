# LSTM Stock Price Prediction

This project aims to predict stock prices using Long Short-Term Memory (LSTM), a type of recurrent neural network (RNN) well-suited for sequential data. The project was completed as part of the final exam for a Deep Learning course.

## Project Overview

Stock price prediction is a complex and challenging task due to the non-linear, sequential nature of stock price movements. By leveraging the capabilities of LSTM, this project focuses on forecasting future stock prices of Amazon and Cisco based on historical data from 1997-2020.

## Dataset
The project uses historical stock price data that includes:
- **Date**: The specific trading date.
- **Close**: The stock's closing price on that date.

Other columns may have been present in the dataset but were not used in this model, which relies on the `Date` and `Close` columns only.

## Project Steps

### 1. Data Preprocessing
   - **Normalization**: The data is normalized to bring all values into a similar range, improving the model's performance.
   - **Training and Testing Split**: The data is split into training and testing sets to evaluate the model’s predictive power on unseen data.
   - **Windowed Dataset Creation**: The data is reshaped to feed into the LSTM model, forming sequences of past prices (windows) to predict the next price.

### 2. Model Architecture
   - **LSTM Layers**: A multi-layer LSTM architecture is used, which helps capture the temporal dependencies in stock prices.
   - **Dense Layer**: A fully connected layer following the LSTM layers outputs the predicted stock price.

### 3. Model Training
   - **Loss Function**: Mean Squared Error (MSE) is used as the loss function to minimize the error between predicted and actual prices.
   - **Optimizer**: The Adam optimizer is chosen for its efficiency in handling gradient-based updates in a complex, sequential model like LSTM.

### 4. Evaluation
   - **Metrics**: The model’s performance is evaluated using Mean Squared Error (MSE), Root Mean Squared Error (RMSE), Mean Absolute Error (MAE) and Mean Absolute Percentage Error (MAPE), providing insights into the accuracy of predictions.
   - **Visualization**: Predicted vs. actual stock prices are plotted to visually inspect the model's performance.

## Results

### 1. Amazon evaluation: 

![image](https://github.com/user-attachments/assets/e6950c90-2b2d-40f9-b327-30181a2bc3fd)

Overall, both models struggled to predict effectively on the test data; however, Model 1 (baseline) performed significantly better across all three datasets. This indicates that both models experienced overfitting, potentially due to the lack of initial scaling.

One reason for overfitting is the absence of scaling on the data. Scaling helps models learn more effectively by normalizing data distributions. Additionally, stock data, such as that from Amazon, tends to be non-patterned and can experience drastic changes, making accurate predictions more challenging.

After modifying the second model by increasing the number of LSTM units, adding Dropout layers, and including an additional LSTM layer, the performance worsened. This suggests that Amazon stock data is better predicted using a simpler architecture.


### 2. Cisco evaluation:

![image](https://github.com/user-attachments/assets/cf691880-6a0f-4ed2-8d92-14062ada96ec)

Based on the results above, the Baseline Model performed significantly better on the Cisco data, achieving good and consistent metric values across the training, validation, and testing sets. Overall, Model 1 (baseline) was able to make accurate predictions on the test data. In contrast, Model 2 experienced overfitting, likely due to the lack of initial scaling.

Modifications to the second model included adding LSTM layers and increasing the number of units in each layer. We can conclude that Cisco data is better predicted using a simpler architecture.

Both datasets demonstrated improved results with simpler architectures compared to the modified, more complex architectures. The modified models became more prone to overfitting.

Overfitting occurs when a model learns specific patterns in the training data too well but fails to generalize effectively to unseen data. This can lead to poor performance on validation and testing datasets.
