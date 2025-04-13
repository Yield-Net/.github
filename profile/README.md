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

## 📊 Returns Projection

### Individual Strategy Returns

\`\`\`math
estimated_return = (investment_amount × allocation_percent ÷ 100) × (expected_apy ÷ 100)
Example: $1000 × 30% × 5.1% = $15.30 annual return
\`\`\`

**Total Portfolio Returns**  
Sum of all strategy returns

Shown in dashboard as:

- Total projected return  
- Risk-weighted return breakdown

---

## 📂 Project Structure

\`\`\`bash
/
├── backend/
│   ├── main.py              # FastAPI entry
│   ├── models/              # DB schemas
│   ├── routers/             # API endpoints
│   ├── services/            # AI & DeFi services
│   └── requirements.txt     # Python deps
├── frontend/
│   ├── app/
│   │   ├── api/             # API proxy
│   │   ├── dashboard/       # Portfolio page
│   │   └── page.tsx         # Landing
│   ├── components/          # UI components
│   ├── lib/                 # Utils (Gemini, Web3, etc.)
│   └── package.json         # Node deps
├── README.md
└── .env files               # For config
\`\`\`

---

## ⚙️ Configuration

**Environment Variables**

**Backend (.env)**

\`\`\`bash
SUPABASE_URL=
SUPABASE_KEY=
GEMINI_API_KEY=
DEFI_LLAMA_API_KEY=
\`\`\`

**Frontend (.env.local)**

\`\`\`bash
NEXT_PUBLIC_BACKEND_URL=
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_KEY=
\`\`\`

---

## 🔐 Security Considerations

- Private keys are never stored – all transactions require explicit user MetaMask confirmation  
- Transaction Transparency – view full on-chain data before confirming  
- Row-level security – enforced in Supabase for multi-user data safety  
- Secure connections – Web3 communications via encrypted RPC providers  

---

## 🧪 API Endpoints

**Authentication**

\`\`\`http
POST /api/login
{ wallet_address: string }
→ { user_id, is_new_user }
\`\`\`

**Profile**

\`\`\`http
POST /api/user-profile
{ profile_data }
→ { success, user_id }
\`\`\`

**Strategy Generation**

\`\`\`http
POST /api/generate-strategy
{ profile_data }
→ [strategy_list]
\`\`\`

**Dashboard**

\`\`\`http
GET /api/dashboard?user_id=
→ { profile, strategies, portfolio }
\`\`\`

**Execution**

\`\`\`http
POST /api/strategy/execute
{ user_address, idx }
→ { transaction_data }
\`\`\`

**AI Assistant**

\`\`\`http
POST /ai-agent/message
{ user_profile, user_message }
→ { ai_response }
\`\`\`

---

## 🗃️ Database Schema (PostgreSQL via Supabase)

**Users**
- id: UUID  
- wallet_address: string  
- email: string?  
- created_at  
- last_login  

**User Profiles**
- id: UUID  
- user_id: UUID  
- risk_tolerance: string  
- investment_amount: float  
- investment_currency: string  
- experience_level: string  
- investment_goals: string[]  
- preferred_activities: string[]  
- investment_horizon: string  

**User Strategies**
- id: UUID  
- user_id: UUID  
- strategy_data: JSON  
- is_active: boolean  
- created_at  
- updated_at  

**User Portfolio**
- id: UUID  
- user_id: UUID  
- asset: string  
- amount: float  

**User Transactions**
- id: UUID  
- user_id: UUID  
- transaction_hash: string  
- blockchain: string  
- protocol: string  
- activity: string  
- amount: float  
- token: string  
- status: string  
- timestamp  

---

## 🛠️ Tech Stack

\`\`\`txt
Layer           Tech
--------------  ------------------------------------------------
Frontend        Next.js 14, React, TypeScript, Tailwind CSS
Backend         FastAPI (Python 3.8+)
AI Assistant    Gemini 2.0 Flash, Gemini 2.5 Pro
Web3/Blockchain ethers.js, Web3.js, MetaMask SDK
Database        PostgreSQL (via Supabase)
Data Feeds      DeFi Llama, CoinGecko
Hosting         Vercel (Frontend), Docker + Uvicorn (Backend)
\`\`\`

---

## 🧑‍💻 Development Setup

**Prerequisites**

- Node.js 16+  
- Python 3.8+  
- MetaMask extension  
- Supabase project  

---

### Backend Setup (FastAPI)

\`\`\`bash
# Navigate to backend directory
cd backend

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys and configuration

# Start the server
uvicorn main:app --reload
\`\`\`

---

### Frontend Setup (Next.js)

\`\`\`bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with your API keys and configuration

# Start the development server
npm run dev
\`\`\`

---

## Future Unimplementation

### Add a Middle Filtering & Validation Layer

- After Gemini returns:  
  - Validate protocol names & chains - currently just LLM searches  
  - Match APY within expected tolerance from live feed  
  - i.e. more validation of APY CLAIMS  

### Add Guardrails (Hardcoded Rules)

- Max 50% allocation per protocol  
- At least 2 different categories  
- Max 1 high-risk protocol unless explicitly allowed  
- Minimum audit/reputation score  

### Build a Strategy Refresh System

- Periodic refresh every X days  
- Auto-rebalance logic  
- Notify user via dashboard or assistant when:  
  - APYs fall significantly  
  - A better opportunity emerges  



