# 💡 DeFi Advisor – AI-Powered Crypto Investment Platform  

![Yield Net Animation](../yield-net-g.gif)

An Ai DeFi assistant that helps users navigate decentralised finance through personalised strategy recommendations and investments controlled by a personalised Ai-Assistant.

---

## 🚀 Features

-  **Web3 Wallet Integration** – Connect via MetaMask for secure authentication and transaction execution
- **Personalised Investment Profiles** – Based on user’s goals, risk tolerance, investment amount, time horizon, and preferences
- **AI-Generated DeFi Strategies** – Smart recommendations using Google Gemini LLM and real-time protocol data
- **Interactive Dashboard** – Monitor strategies, track performance, visualise risk and returns
- **Conversational AI Assistant** – Get answers, portfolio updates, or strategy recommendations via natural language
- **Smart Contract Execution** – Direct integration with Ethereum-based DeFi protocols via MetaMask
- **Adaptive Portfolio Management** – Strategies update dynamically based on user changes or market trends

---

## 🧠 How We Recommend Trades

Our system generates personalised DeFi investment strategies using live data and AI, with a focus on Ethereum-based lending and staking opportunities.

### Inputs

- **User Profile**
  - Risk tolerance
  - Investment goals
  - Amount & currency
  - Time horizon
  - Experience level
  - Preferred DeFi activities

- **Market Data** (via [DeFi Llama](https://defillama.com))
  - Protocols on Ethereum only
  - Status: Active
  - TVL > $1M
  - Categories: Lending, Staking
  - Matches user’s preferred activities (if specified)

---

### Strategy Generation Flow

1. **Filter & Rank Protocols**
   - Filter DeFi Llama data:
     - Ethereum protocols
     - Active status
     - TVL > $1M
     - Staking or lending category
   - Rank by:
     - Total Value Locked (TVL)
     - Reputation & historical APY
     - Fit with user risk/goals
     - Compatibility with user experience

2. **Prompt AI for Strategy**
   - Construct prompt from user profile + ranked protocols
   - Send to Gemini 2.0 Flash model
   - AI returns structured JSON:
     - Protocol name
     - Activity (staking, lending)
     - Token
     - Allocation %
     - Expected APY
     - Estimated return
     - Risk level
     - Justification

3. **Evaluate & Present**
   - Ensure:
     - Portfolio allocations sum to 100%
     - APY-to-risk is favourable
     - Diversification and goal alignment
   - Display as cards in dashboard with charts and execution buttons

---

## 🧭 User Flow

1. **Connect Wallet**
   - Authenticate with MetaMask wallet

2. **Create Investment Profile**
   - Complete questionnaire:
     - Risk tolerance
     - Goals
     - Preferred activities
     - Experience level
     - Investment amount and currency
     - Time horizon

3. **Receive AI-Powered Strategy Recommendations**
   - AI generates detailed DeFi strategies
   - Includes rationale and risk analysis

4. **Explore Dashboard**
   - View:
     - Profile summary
     - Allocation pie chart
     - APY bar chart
     - Strategy cards
     - Performance over time

5. **Execute Strategies**
   - One-click execution via MetaMask
   - View transaction hash and status

6. **Chat with Assistant**
   - Conversational AI interface
   - Ask for clarifications or update your profile
   - Receive new strategy recommendations

---


