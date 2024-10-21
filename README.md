# Amazon Stock Analysis Project

## Overview
This project aims to analyze the stock performance of Amazon.com, Inc. (Ticker: AMZN) using the `yfinance` library. By leveraging this library, we can retrieve comprehensive financial data, including stock prices, earnings, and other relevant metrics. The goal is to visualize Amazon's stock trends, evaluate its financial health, and derive insights into its market performance.

## Purpose
The primary purpose of this project is to provide a detailed analysis of Amazon's stock performance over time. This includes:

- Retrieving and displaying key financial information about Amazon.
- Analyzing quarterly earnings data.
- Visualizing stock price changes and trading volume over specific periods.
- Calculating daily returns and determining trends based on stock price fluctuations.

## Goals
1. **Data Retrieval**: Use the `yfinance` library to fetch Amazon's stock data and financial information.
2. **Data Analysis**: Analyze key financial metrics, including revenue, earnings, and margins.
3. **Visualization**: Create visual representations of stock price changes and trading volumes.
4. **Trend Analysis**: Classify daily returns into various trend categories to assess market behavior.

## Installation
To run this project, ensure you have Python and the required libraries installed. You can install the necessary libraries using pip:

```bash
pip install yfinance pandas matplotlib
```

## Usage
### Retrieving Financial Information
The following code snippet retrieves and displays key financial information about Amazon:

```python
import yfinance as yahooFinance

# Get information about Amazon
GetAmazonInformation = yahooFinance.Ticker("AMZN")

# Display key-value pairs of financial information
for key, value in GetAmazonInformation.info.items():
    print(key, ':', value)
```

### Analyzing Quarterly Earnings
To examine Amazon's quarterly earnings data, use:

```python
# Display quarterly earnings data
print(GetAmazonInformation.quarterly_earnings)
```

### Downloading Historical Stock Data
You can download historical stock data for Amazon as follows:

```python
import yfinance as yf

# Download historical stock data
df = yf.download('AMZN')
df.to_excel('amzn.xlsx')  # Save data to an Excel file
```

### Visualizing Stock Price Changes
To visualize the change in Amazon's stock price over time:

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(16,8))
plt.title("Change in Stock Price")
plt.plot(df['Close'])
plt.xlabel('Date', fontsize=18)
plt.ylabel('Close Price', fontsize=18)
plt.grid()
plt.show()
```

### Analyzing Daily Returns
You can calculate daily returns and classify trends based on those returns:

```python
df['Daily_returns'] = df['Close'] - df['Open']

def trend(x):
    if x > -0.5 and x <= 0.5:
        return 'Slight' or 'No change'
    elif x > 0.5:
        return 'Slight Positive'
    elif x < -0.5:
        return 'Slight Negative'
    # Additional conditions...

df['Trend'] = df['Daily_returns'].apply(lambda x: trend(x))
```

### Visualizing Trend Frequency
To visualize the frequency of trends in a pie chart:

```python
pie_data = df.groupby('Trend').size()
plt.pie(pie_data, labels=pie_data.index, autopct='%1.1f%%')
plt.title('Trend Frequency')
plt.show()
```

## Conclusion
This project serves as an analytical tool for investors and analysts interested in understanding Amazon's stock performance. By utilizing the `yfinance` library, users can access a wealth of financial data and generate insightful visualizations to inform their investment decisions. 

