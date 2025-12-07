# **Qubic Sentinel 📊**

### **AI-Powered Real-Time Market Intelligence for the Qubic Network**

## **📖 Overview**

**Qubic Sentinel** is an institutional-grade market intelligence terminal built specifically for the **Qubic Network**. Unlike standard block explorers that display raw, context-less data, Sentinel leverages generative AI to analyze the *intent* and *psychology* behind every major transaction in real-time.

By filtering out retail noise and focusing on institutional-grade volume (\>50M QUBIC), Sentinel provides traders, ecosystem founders, and liquidity providers with instant signals on accumulation and distribution events.

## **🏗️ Architecture & Tech Stack**

This project utilizes a **Serverless, Event Driven Architecture** to achieve high availability and sub-second latency without traditional backend maintenance.

| Component | Technology | Role in Architecture |
| :---- | :---- | :---- |
| **Ingestion Layer** | **EasyConnect** | Listens to the Qubic blockchain for specific smart contract events (AddToBidOrder, AddToAskOrder). |
| **Orchestration** | **Make.com** | Handles ETL (Extract, Transform, Load) logic and manages parallel pipelines for "Buy" vs "Sell" logic. |
| **Intelligence Engine** | **Google Gemini 1.5 Pro** | Generates distinct analysis of "Accumulation" vs "Dumping" using specialized financial system prompts. |
| **Real-Time DB** | **Google Sheets** | Acts as a high-speed, structured database for the frontend visualization layer. |
| **Visualization** | **Google Looker Studio** | Renders the "War Room" dashboard with real-time volatility charts and AI feeds. |
| **Alerting System** | **Discord Webhooks** | Pushes instant "Flash Alerts" to mobile devices with \<500ms latency. |


## **⚡ Key Features**

### **1\. The "AI Analyst"**

Every transaction is processed by **Gemini 1.5 Pro** before it hits the dashboard. Instead of just displaying "Buy: 75M QUBIC," the system generates a strategic assessment such as:

*"Massive accumulation detected at the 1200 support level; confirming institutional entry ahead of a potential breakout."*

### **2\. Dual-Pipeline Visualization**

The system separates market pressure into distinct visual streams on the main volatility chart:

* **🔵 Blue Spikes:** Institutional Accumulation (Buy Pressure).  
* 🔴 Red Spikes: Whale Dumping (Sell Pressure).  
  This allows for instant visual identification of market sentiment shifts.

### **3\. Smart Noise Filtering**

Optimized for Qubic's high-supply tokenomics. The system employs a **50,000,000 QUBIC Threshold** to filter out retail dust, ensuring the dashboard only updates for significant market-moving events.

## **📂 Repository Structure**

* /blueprints \- JSON exports of the Make.com orchestration scenarios (Buy Pipeline & Sell Pipeline).  
* /prompts \- The exact system prompts used to condition Gemini 1.5 Pro for financial analysis.  
* /assets \- Architecture diagrams and screenshots of the active dashboard.

## **🚀 Live Demo**

Access the live intelligence dashboard here:  
🔗 [Qubic Sentinel Terminal](#https://lookerstudio.google.com/reporting/3a577c8d-cd5b-4e4a-ad1e-be72941c67e6)

## **🛠️ How to Build**

To deploy your own instance of Qubic Sentinel:

1. **Import Blueprints:** Upload the .json files from the /blueprints folder into a new Make.com scenario.  
2. **Database Setup:** Create a Google Sheet with headers: Timestamp, Type, Sender, VOL(QUBIC), AI\_Analysis.  
3. **Ingestion:** Configure **EasyConnect** to send AddToBid and AddToAsk events to your Make.com webhook URL.  
4. **Connect Intelligence:** Add your Google Gemini API key to the Make.com module.  

## 

Submitted for **Qubic Hack the Future**.

* **Track:** EasyConnect Integrations (Track 2).  
* **Focus:** Leveraging EasyConnect's real time event stream to build a production-ready analytical tool.