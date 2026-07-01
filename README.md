# mt5-api

MT5 Broker API Connector Codebase  
*https://angrybroker.com/*

---

> Run your own forex brokerage without expensive third-party providers. Eliminate monthly fees and save thousands $.  
> No need to pay monthly fees to other companies for API access | Bonus Trader Room mockups included!

---

## System Architecture — Component Breakdown

### 1. Web Services Component (REST API Middleware)

- **Role:** Mediates between the MT5 DLL wrapper and your trader's room frontend.
- **Protocol:** RESTful API endpoints over HTTP/HTTPS.
- **Capabilities:**
  - Account lifecycle management (create, suspend, delete, balance adjustments)
  - Real-time trading operations (market/limit/stop orders, position management)
  - Live price streaming and historical data retrieval
  - Webhook support for third-party integrations
- **Tech Stack:** PHP / Node.js / Python (implementation agnostic)

---

### 2. MT5 DLL Binary Wrapper (Core Bridge)

- **Role:** Low-level C++ bridge that encapsulates MetaTrader 5's proprietary DLL methods.
- **Key Features:**
  - Clean, type-safe C++ interfaces for all native MT5 functions
  - Thread-safe connection pooling
  - Error logging and fault tolerance
  - Exposed methods include: `TradeOpen()`, `TradeClose()`, `AccountInfo()`, `MarketWatch()`, `HistoryFetch()`
- **Output:** Compiled `.dll` (Windows) with documented headers for easy integration.

---

### 3. Client Windows Application (MT5 Terminal Emulator)

- **Role:** Lightweight desktop agent that mimics MT5 terminal behavior for automated execution.
- **Triggered by:** PHP scripts (via CLI or scheduled tasks) to execute trades and fetch market snapshots.
- **Features:**
  - Headless operation mode (no GUI required)
  - Supports both live and demo environment switching
  - Handles symbol subscription and tick data caching
  - Can run as a Windows service for 24/7 reliability
- **Communication:** Uses named pipes or local sockets to talk to the DLL wrapper.

---

| **Angry Broker** | **Focus** |
|-------------|-----------|
| **For Developers** | "Self-contained MT5 API stack — wrapper, REST layer, and terminal emulator in one repo." |
| **For Business Owners** | "Cut out the middleman. Host your own MT5 broker backend with zero per-trade fees." |
| **For SysAdmins** | "Deployable MT5 bridge solution with minimal dependencies and simple configuration." |
| **For Traders** | "Behind every trade, our API ensures low-latency execution — no third-party slowdowns." |
