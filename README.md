# 🔄 Asynchronous Market Data Pipeline (Personal Learning Project)

### ⚠️ Project Context
This repository contains a Jupyter Notebook documenting my personal journey to master **advanced asynchronous Python** and **real-time data ingestion**. 

My goal was **not** to build a commercial trading system or a quantitative finance product. Instead, I challenged myself to use AI-assisted development ("Vibe Coding") to engineer a resilient, non-blocking data pipeline from scratch that connects to external WebSockets, processes streaming JSON, and logs it safely into a local database for post-market auditing.

---

## 🛠️ Technical Concepts Explored & Implemented

- **Asynchronous Concurrency (`asyncio` & `aiohttp`):** Learned how to maintain persistent WebSocket connections to stream real-time market data (L2 Order Books, Candlesticks) alongside REST API calls without blocking the main execution thread.
- **Vectorized Data Processing (`pandas` & `numpy`):** Applied fast, vectorized mathematical operations to streaming data to calculate volatility metrics (ATR) and structural zones in real-time.
- **Local Data Persistence (`sqlite3`):** Designed a relational schema ("The Vault") to log streaming data and generated signals, ensuring zero data loss during network spikes and enabling historical querying.
- **Resilient Error Handling:** Implemented network diagnostic tools, graceful `KeyboardInterrupt` exits, and strict JSON parsing fallbacks to prevent pipeline crashes.
- **AI-Assisted Development:** Leveraged LLMs as a pair-programmer to understand the complexities of the `asyncio` event loop, debug WebSocket disconnection errors, and structure the database schema efficiently.

---

## 📂 Notebook Architecture (Modular Design)

1. **Module 0: Audit Vault Initialization** – Sets up the local `sqlite3` database for persistent logging of signals and executed actions.
2. **Module 1 & 8: Network & API Diagnostics** – Pre-flight checks to validate WebSocket connectivity and API health before initiating heavy data streams.
3. **Module 2: Multi-Timeframe Macro Validator** – Fetches and processes historical REST data to establish baseline structural bias (non-blocking).
4. **Module 3: Async Signal Scanner** – The core loop. Concurrently scans multiple assets via WebSocket/REST, calculates metrics, and logs high-probability structural setups to the database.
5. **Module 4: Execution Monitor** – A real-time state machine that tracks active conditions, manages kill-switches, and logs final outcomes with duration metrics.
6. **Module 5 & 6: Post-Market Audit** – Retroactively fetches missing high-resolution data (e.g., 1m wicks, 4h trends) to validate the accuracy of the initial signal against market reality, exporting clean reports to Excel.

---

## 💡 Key Takeaway

This project proved my ability to take complex, abstract technical concepts (like async concurrency and WebSocket state management), break them down using business logic, and use AI to execute and deploy a functional, resilient data system. 

*Note: This is a personal engineering project focused on data pipeline architecture and system reliability. It is not financial advice nor a commercial financial product.*
