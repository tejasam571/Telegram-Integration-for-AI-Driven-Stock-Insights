##📈 AI-Powered Day Trading Agent with n8n
Fully automated stock analysis and trade recommendation bot using Telegram, OpenAI, TwelveData API, and Newsdata API — no self-hosting required.

#✅ What This Project Does
This project builds an AI Agent that:

Accepts a stock symbol via Telegram (e.g., TSLA)

Retrieves recent candlestick data and news sentiment

Analyzes technical indicators (RSI, MACD)

Uses OpenAI to generate trade signals (Buy/Sell/Hold) with:

Entry Price

Stop Loss

Target Exit Price

Sends final recommendation back to Telegram – in real time!

⚙️ Tech Stack Used
n8n – no-code workflow automation platform

Telegram Bot – User interface for input/output

TwelveData API – To fetch real-time candlestick data

Newsdata.io API – To get latest news articles about the stock

OpenAI API (GPT-4.1) – To evaluate sentiment and generate trade recommendations

JavaScript (in n8n) – For data cleaning, aggregation, and formatting

🧠 How It Works — Step-by-Step
1. Telegram Trigger
User sends a message like TSLA (stock ticker) in Telegram.

This triggers the n8n workflow instantly.

2. Fetch Candlestick Data
n8n sends 3 parallel HTTP requests to TwelveData API to retrieve:

1-minute candles

15-minute candles

1-hour candles

Each API call returns OHLCV (Open, High, Low, Close, Volume) data.

3. Merge & Structure Candlestick Data
A Merge node combines all 3 timeframes.

Aggregate node arranges them into a single object.

A JavaScript Code node formats this data to be AI-ready.

4. Fetch News Articles
The stock ticker is passed to the Newsdata API.

This fetches the last 24 hours of news about the company.

The data is passed through another JavaScript node to clean up unwanted metadata and keep only:

Headline

Date

Description

5. Analyze News Sentiment
The cleaned news headlines are sent to OpenAI (GPT-4.1) using a Chat node in n8n.

The model evaluates each article as:

Positive

Neutral

Negative

Output includes a rationale to support the classification.

6. Aggregate Sentiment + Candlestick Data
Another Merge node combines:

News sentiment summary

Candlestick data

The final structured data contains:

Stock ticker

All timeframes' candles

News sentiment count and score

7. AI Agent Trade Decision
The combined data is passed into a new OpenAI GPT-4.1 prompt.

The AI is prompted with:

“Based on this data, should I Buy/Sell/Hold this stock?”

“Give entry, stop loss, and target prices.”

The model generates a clean, concise trade signal.


