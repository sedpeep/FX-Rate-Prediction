
# FX Rate Prediction Using LSTM and Random Forest

This project aims to predict future currency exchange rates using machine learning models, specifically an LSTM neural network and a Random Forest regressor. The dataset contains historical exchange rates and COVID-19 policy data from the OxCGRT dataset. The models are trained to forecast upcoming rates based on past trends and policy changes.

## Dataset

### Currency Exchange Rate Dataset

The dataset `FX_FanU.xlsx` contains historical exchange rates for various currencies against the USD. It includes the following currencies:
- Canadian Dollar (CAD)
- Euro (EUR)
- British Pound (GBP)
- Japanese Yen (JPY)
- Swedish Krona (SEK)
- Singapore Dollar (SGD)

### OxCGRT Dataset

The OxCGRT dataset contains COVID-19 policy measures for G10 countries and Singapore. This dataset is used to understand the impact of COVID-19 policies on currency exchange rates.

## Preprocessing

1. **Filtering and Cleaning**: The exchange rate dataset is filtered to include only the columns related to the interested currencies. The OxCGRT dataset is filtered to include only G10 countries and Singapore, and specific columns are retained while others are dropped.
2. **Date Conversion**: The date formats are standardized, and the datasets are merged based on the date.
3. **Normalization**: Data is normalized using `MinMaxScaler`.

## Model Training

### LSTM Model

The LSTM model is used to capture the sequential nature of exchange rates. It is trained on the exchange rate data.

- **Sequence Length**: 5
- **Hidden Size**: 50
- **Output Size**: 1
- **Optimizer**: Adam
- **Loss Function**: MSELoss

### Random Forest Model

The Random Forest model is trained on a combination of predicted exchange rates from the LSTM model and COVID-19 policy data.

- **Number of Estimators**: 200
- **Features Used**: COVID-19 policy measures and predicted exchange rates

## Evaluation

The models are evaluated using Mean Squared Error (MSE) and visualized through plots comparing the actual and predicted exchange rates.

## Instructions

### Running the Project

1. **Install Dependencies**: Ensure you have the necessary Python packages installed. Use the following command:
    ```bash
    pip install numpy pandas matplotlib scikit-learn torch openpyxl shap statsmodels
    ```

2. **Load the Datasets**: Place the `FX_FanU.xlsx` and `OxCGRT_compact_national_v1.csv` files in the same directory as the script.

3. **Run the Script**: Execute the script to preprocess the data, train the models, and evaluate their performance.

### Saving and Loading Models

- **Save Model**: The trained LSTM model is saved using `torch.save(model.state_dict(), 'model.pth')`.
- **Load Model**: To load the saved model, use `model.load_state_dict(torch.load('model.pth'))`.

### Generating Predictions

- **LSTM Model**: Generates initial predictions for exchange rates.
- **Random Forest Model**: Refines the predictions using COVID-19 policy data.

### Visualizing Results

- The script generates plots comparing actual and predicted exchange rates.
- SHAP values are used to explain feature importance for the Random Forest model.

## Files

- `FX_FanU.xlsx`: Currency exchange rate dataset.
- `OxCGRT_compact_national_v1.csv`: OxCGRT dataset.
- `lstm_model.pth`: Saved LSTM model.
- `rf_model_predictions.csv`: Predictions from the Random Forest model.
- `currency_policy.csv`: Processed policy data for the selected country.

## Conclusion

This project demonstrates the use of sequential LSTM models and Random Forest regressors to predict currency exchange rates, incorporating the impact of external factors such as COVID-19 policies. The combination of these models provides a comprehensive approach to forecasting in volatile environments.
