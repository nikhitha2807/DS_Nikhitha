# DS_Nikhitha
"Data science assignment analyzing trader behavior vs Bitcoin market sentiment (Fear/Greed)."

# Trader Behavior vs Bitcoin Market Sentiment (Fear & Greed Analysis)

This project analyzes how Bitcoin market sentiment (Fear, Greed, Extreme Fear, Extreme Greed, Neutral) influences a trader’s performance.
It combines market psychology with real trading data to uncover actionable insights.

 ## Tech Stack

Python (Pandas, Matplotlib)

Google Colab

Data Cleaning & Preprocessing

Data Visualization

Statistical Analysis

## Dataset Download Links

The original datasets (too large for GitHub) can be downloaded from Google Drive:

Trader Data:
https://drive.google.com/drive/folders/1B5OMHH29mvq9o8XnrkHZJX9D9gBp57Ds?usp=drive_link

Fear & Greed Index:
https://drive.google.com/drive/folders/1sM4J3NxFRFyknykpohg8uHmO-fP8AinZ?usp=drive_link

# Project Structure
DS_Nikhitha/
│── notebook_1.ipynb               # Full code and analysis workflow
│── merged_data_small.csv          # Clean, compressed merged dataset
│── README.md                      # Project documentation
│── images/                        # Visualizations (graphs)
       ├── profit_sentiment.png
       ├── volume_sentiment.png
       └── trade_count_sentiment.png

## Project Overview

This project investigates the relationship between market sentiment and trader performance.

It includes:

✔ Downloading large datasets
✔ Cleaning both datasets
✔ Time conversion (timestamps → dates)
✔ Merging sentiment data with trading data
✔ Calculating profit, volume, and frequency by sentiment
✔ Visualizing the results

# Files Included
## notebook_1.ipynb

Contains the full workflow:

Dataset download using gdown

Data cleaning & renaming

Merging datasets

Exploratory Data Analysis (EDA)

Graph creation (profit, volume, count)

## merged_data_small.csv

A compressed, clean version of the merged file.
Useful for:

Quick preview

Re-analysis

Uploading to GitHub without file-size issues

## Graphs
Average Profit – Fear vs Greed
<img width="571" height="546" src="https://github.com/user-attachments/assets/58c2c55c-3e9d-4858-bc17-6851dea92940" />
Trading Volume – Fear vs Greed
<img width="554" height="546" src="https://github.com/user-attachments/assets/157d95bb-2305-4a7a-81d9-fafaffb12bc5" />
Number of Trades – Fear vs Greed
<img width="589" height="546" src="https://github.com/user-attachments/assets/a769886f-3c49-4258-babe-412dc95820a1" />

## How the Data Was Merged
Step 1 — Convert timestamps to date
sentiment['date'] = pd.to_datetime(sentiment['timestamp'], unit='s').dt.date
trader['date'] = pd.to_datetime(trader['Timestamp IST'], errors='coerce').dt.date

Step 2 — Merge sentiment with trading data
merged = trader.merge(sentiment[['date', 'classification']], on='date', how='left')

Step 3 — Rename headings
merged = merged.rename(columns={
    "Closed PnL": "closedPnL",
    "Size Tokens": "size_tokens",
    "Size USD": "size_usd",
    "Execution Price": "execution_price",
    "Timestamp IST": "timestamp_ist"
})

Step 4 — Analysis performed

Average profit per sentiment

Total traded volume per sentiment

Number of trades per sentiment

Step 5 — Visualizations

Three bar charts were created:

Average Profit – Fear vs Greed

Trading Volume – Fear vs Greed

Number of Trades – Fear vs Greed

### Results Summary

This analysis answers key questions:

✔ Does the trader earn more during Greed or Fear days?
✔ Which sentiment results in the highest trading activity?
✔ How does market psychology influence profit and volume?

Understanding these patterns helps evaluate whether the trader performs better during:

⚡ High-confidence (Greed) periods
🔥 Panic (Fear) periods
📉 Extreme market conditions

### Future Improvements

Build a machine learning model to predict profit using sentiment

Add a time-series trend analysis

Create an interactive dashboard using Streamlit or Power BI

Calculate rolling averages (7-day, 30-day) for deeper insight

## Conclusion

This project demonstrates how market emotions impact real trading decisions.
By combining sentiment indicators with actual trade records, we gain a clear view of how behavior changes based on Fear, Greed, and Neutral conditions.

It showcases skills in data merging, analysis, visualization, and storytelling with data.
