# 📈 AI-Powered Day Trading Agent with n8n

Fully automated stock analysis and trade recommendation bot using **Telegram**, **OpenAI**, **TwelveData API**, and **Newsdata API** — no self-hosting required.

---

## ✅ What This Project Does

This project builds an **AI Agent** that:

- Accepts a stock symbol via **Telegram** (e.g., `TSLA`)
- Retrieves recent **candlestick data** and **news sentiment**
- Analyzes technical indicators (**RSI**, **MACD**)
- Uses **OpenAI** to generate trade signals:  
  ➤ Buy / Sell / Hold  
  ➤ Entry Price  
  ➤ Stop Loss  
  ➤ Target Exit Price  
- Sends the final recommendation back to Telegram – **in real time**

---

## ⚙️ Tech Stack Used

- **n8n** – no-code workflow automation platform
- **Telegram Bot** – user interface for input/output
- **TwelveData API** – fetch real-time candlestick data
- **Newsdata.io API** – fetch latest news articles
- **OpenAI API (GPT-4.1)** – evaluate sentiment & generate trade recommendations
- **JavaScript (inside n8n)** – data cleaning, aggregation & formatting

---

## 🧠 How It Works — Step-by-Step

### 1. Telegram Trigger
- User sends a message like `TSLA` (stock ticker) in Telegram  
- This triggers the **n8n workflow** instantly

### 2. Fetch Candlestick Data
- n8n sends 3 parallel HTTP requests to TwelveData API to retrieve:
  - 1-minute candles
  - 15-minute candles
  - 1-hour candles
- Each API returns OHLCV data (Open, High, Low, Close, Volume)

### 3. Merge & Structure Candlestick Data
- A **Merge** node combines all 3 timeframes
- **Aggregate** node organizes the data
- A **JavaScript Code** node formats it for AI input

### 4. Fetch News Articles
- The ticker is passed to **Newsdata.io API**
- Retrieves latest news (last 24 hours)
- Data is cleaned using JavaScript to keep:
  - Headline
  - Date
  - Description

### 5. Analyze News Sentiment
- Headlines sent to **OpenAI GPT-4.1** via Chat node
- Model classifies each article as:
  - Positive
  - Neutral
  - Negative
- Returns reasoning behind classification

### 6. Aggregate Sentiment + Candlestick Data
- Another **Merge** node combines:
  - Candlestick analysis
  - News sentiment summary
- Final structured format is created

### 7. AI Agent Trade Decision
- Combined data passed to OpenAI again
- AI generates decision prompt:  
  _"Based on this data, should I Buy/Sell/Hold this stock?"_
- Includes: **entry price, stop loss, target price**

### 8. Send Back to Telegram
- AI recommendation sent back to the user via Telegram

#### 🧾 Example Output


<img width="871" height="167" alt="Screenshot 2025-07-13 011938" src="https://github.com/user-attachments/assets/ebe01275-c78e-4d44-90f5-7eeb2148708a" />

---

## 📌 Key Highlights

- 🔁 **Real-time interaction** — no cloud hosting needed
- ✅ Simple **API integration** (TwelveData, Newsdata, OpenAI)
- 🧠 AI-powered, **customizable** workflow via n8n
- 🧩 **Modular design** — easily add indicators or exchanges
- 💬 Works **entirely through Telegram**

---

## 📥 How to Use (Quick Setup)

1. **Create a Telegram bot** via [BotFather](https://t.me/BotFather)
2. Connect it in n8n using the **Telegram Trigger** node
3. Get API keys:
   - [TwelveData](https://twelvedata.com/)
   - [Newsdata.io](https://newsdata.io/)
   - [OpenAI](https://platform.openai.com/)
4. Import the `AI_Trader_Workflow.json` into n8n
5. Add your API keys to the HTTP request nodes
6. Send stock tickers like `AAPL` or `TSLA` via Telegram — and receive recommendations!

---

## 🧠 Visual Overview
![WhatsApp Image 2025-07-13 at 00 44 32_4f0c4339](https://github.com/user-attachments/assets/6d536300-e94d-4269-9b98-233c19cfd5eb)

![WhatsApp Image 2025-07-13 at 00 46 23_e6935801](https://github.com/user-attachments/assets/3735c53e-6567-418b-80a2-db770906976e)

![WhatsApp Image 2025-07-13 at 00 48 01_79b33ec5](https://github.com/user-attachments/assets/5c0d63c7-f394-4b49-87c9-8927f9c70dd4)

<img width="3560" height="3312" alt="Building a Profitable AI Day Trading Agent" src="https://github.com/user-attachments/assets/8a264012-abfb-4241-9926-11a51cd4555e" />


---

## 🤝 Let’s Collaborate

If you're exploring AI agents or trading bots using **n8n**, feel free to connect or fork this repo!  
DM or open an issue if you need help with setup or want the `.json` file.

---

## 🔖 Tags

#n8n #AItrading #OpenAI #GPT4 #TelegramBot #NoCode #StockMarket  
#Fintech #NewsSentiment #DayTrading #Automation #TejasLearnsAI
