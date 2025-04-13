






## 📈 How We Recommend Trades

Our system generates personalised DeFi investment strategies using live data and AI, focusing on long-term, Ethereum-based opportunities in lending and staking.

### Inputs
- **User Profile**: risk tolerance, goals, investment amount, horizon, experience, activity preferences.
- **Market Data**: pulled from [DeFi Llama](https://api.llama.fi/protocols), filtered for:
  - Active protocols
  - Ethereum chain
  - TVL > $1M
  - Lending or staking categories

### Strategy Generation
1. **Filter and Rank Protocols**
   - Filter DeFi Llama data to include only:
     - Protocols on Ethereum
     - Status: Active
     - TVL > $1M
     - Categories: Lending, Staking
     - Matches user’s preferred DeFi activities (if specified)
   - Rank protocols based on:
     - Total Value Locked (TVL) — proxy for trust and liquidity
     - Compatibility with user's experience level and risk tolerance
     - Alignment with investment goals (e.g. stable protocols for passive income)
     - Historical APY trends (where available)
   - Return top 20 ranked protocols to inform AI prompt

2. Construct a prompt and send to Gemini AI (`gemini-1.5-pro-latest`).

3. AI returns JSON strategy including:
   - Protocol
   - Activity type
   - Token
   - Allocation %
   - Expected APY
   - Estimated return
   - Risk level
   - Justification

### ✅ Evaluation Criteria
- Matches user’s goals and risk profile
- Favourable APY-to-risk ratio
- Protocol reputation and TVL
- Diversified allocation summing to 100%

Only the top 20 relevant protocols are considered per user request.
