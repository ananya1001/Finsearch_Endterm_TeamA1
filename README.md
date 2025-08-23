# Testing the Black-Scholes Model with Nifty50 Data

This project was developed to assess the accuracy of the theoretical Black-Scholes option pricing model. It compares the model's calculated prices to real-world market prices of Nifty50 index options, using historical data from August 6th, 2025, from the National Stock Exchange (NSE) of India.

Our first step was data cleaning, where we extracted a raw NSE options data file and filtered out only the relevant Nifty50 option contracts. Then, we fed the cleaned data into our script that calculates the Black-Scholes price for each option and computes its accuracy using different key metrics.

## File Structure
* `original_dataset.csv`: The raw, unmodified options data file (Bhavcopy) from the NSE.
* `dataset_cleaner.ipynb`: The Jupyter Notebook used to clean the raw data.
* `main.ipynb`: The Jupyter Notebook that performs the Black-Scholes analysis on the cleaned data.
* `cleaned_nifty_options.csv`: The output of the cleaning script, which serves as the input for the analysis script.

### 1. Data Cleaning (`dataset_cleaner.ipynb`)
This script is the first step in the process. It performs the following actions:
* Loads the raw data from `original_dataset.csv`.
* Filters the thousands of contracts to isolate only those for the 'NIFTY' index.
* Parses the complex contract name string (e.g., `OPTSTKCDSL28-AUG-2025CE1580`) to extract key parameters:
    * Expiry Date
    * Strike Price
    * Option Type (Call/Put)
* Cleans the dataset by removing contracts with no trading volume or missing price data.
* Saves the final, analysis-ready data into `cleaned_nifty_options.csv`.

### 2. Black-Scholes Analysis (`main.ipynb`)
This is the core of the project. We used the cleaned data to:
* Calculate the theoretical option price for each contract using the Black-Scholes formula.
* Compare the calculated price to the actual market price from the dataset.
* Compute and display three key accuracy metrics:
    * **Mean Absolute Error (MAE):** The average absolute difference between the predicted and actual prices. A lower MAE indicates a more accurate model on average.
    * **Root Mean Squared Error (RMSE):** A measure of error that gives more weight to larger discrepancies.
    * **R-squared (R²):** A statistical measure of how well the model's predictions explain the variance in the market prices (a value of 1.0 indicates a perfect fit).
