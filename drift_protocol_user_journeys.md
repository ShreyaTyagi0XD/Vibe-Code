# Drift Protocol User Journey Flows

Based on official documentation from https://docs.drift.trade/ and https://app.drift.trade

---

## User Journey Flow 1: Trading Perpetuals on Drift Protocol

### Pre-Journey Requirements
- User has basic knowledge of cryptocurrency and DeFi
- User has access to a computer/mobile device with internet
- User has some cryptocurrency (SOL/USDC) to start trading

### Journey Overview
**Goal**: Successfully execute a perpetual futures trade on Drift Protocol
**User Type**: New to intermediate crypto trader
**Duration**: 15-30 minutes (first time setup)

---

### Phase 1: Setup & Onboarding (5-10 minutes)

#### Step 1: Wallet Setup
**Action**: Download and configure Solana wallet
- Visit phantom.app/download (recommended wallet)
- Install browser extension (Chrome/Brave/Firefox/Edge)
- Create new wallet with secure password
- **Critical**: Write down and securely store 12-word seed phrase
- **Security Note**: Never share seed phrase with anyone

#### Step 2: Acquire SOL
**Action**: Get SOL for transaction fees
- Purchase SOL on CEX (Binance, Coinbase, Kraken)
- Withdraw SOL to Phantom wallet address
- Alternative: Bridge assets from other chains using recommended bridges
- **Minimum**: ~0.1 SOL for fees and account setup

#### Step 3: Access Drift
**Action**: Connect to Drift Protocol
- Navigate to app.drift.trade
- Click "Connect Wallet" (top right)
- Select Phantom wallet
- Sign wallet connection message
- **One-time fee**: 0.035 SOL for account initialization

---

### Phase 2: Account Setup & Funding (5-10 minutes)

#### Step 4: Initial Deposit
**Action**: Fund trading account
- Click "Deposit" button (top right)
- Choose asset: USDC (recommended) or SOL
- Enter deposit amount (start with $100-500 for testing)
- Confirm transaction in wallet
- **Supported Collateral**: USDC, SOL, BTC, ETH (cross-collateral system)

#### Step 5: Account Overview
**Action**: Familiarize with interface
- Review "Overview" tab showing:
  - Portfolio value and balance history
  - Account health status
  - Available markets
  - Current positions (none yet)
- Check "Balances" page for deposited collateral
- **Key Metric**: Free collateral available for trading

---

### Phase 3: Market Analysis & Trading (10-15 minutes)

#### Step 6: Market Selection
**Action**: Choose perpetual market
- Navigate to "Markets" section
- Review available perp markets (SOL-PERP, ETH-PERP, BTC-PERP, etc.)
- Analyze market data:
  - Oracle price vs Mark price
  - 24h volume and price change
  - Funding rate (positive = longs pay shorts)
  - Open interest
- **Popular choice**: SOL-PERP for beginners

#### Step 7: Position Planning
**Action**: Determine trade parameters
- Decide direction: Long (bullish) or Short (bearish)
- Calculate position size based on risk tolerance
- Consider leverage (1x to 101x available)
- **Risk Management**: Start with lower leverage (2x-5x)
- Check liquidation price estimates

#### Step 8: Order Placement
**Action**: Execute the trade
- Click on chosen market (e.g., SOL-PERP)
- Select order type:
  - **Market Order**: Immediate execution
  - **Limit Order**: Specific price target
  - **Stop Loss/Take Profit**: Risk management
- Enter:
  - Position size (in USD notional or asset amount)
  - Leverage multiplier
  - Order type specific parameters
- Review trade summary:
  - Entry price estimate
  - Trading fees (typically 0.1% for takers)
  - Resulting leverage and margin requirement
- **Execute**: Confirm transaction

---

### Phase 4: Order Execution & Management (2-5 minutes)

#### Step 9: Order Processing
**System Process**: Drift's unique execution flow
- Order enters 5-second Dutch auction (JIT system)
- Market makers compete to fill at better prices
- If no JIT liquidity: Order filled against AMM
- Alternatively: Matched with limit orders on DLOB
- **User sees**: Order status updates in real-time

#### Step 10: Position Monitoring
**Action**: Track active position
- View position in "Positions" tab:
  - Entry price, current mark price
  - Unrealized P&L (real-time)
  - Position size and leverage
  - Estimated liquidation price
- Monitor funding payments (paid/received hourly)
- Track account health and free collateral

---

### Phase 5: Position Management & Exit (Variable)

#### Step 11: Position Adjustments (Optional)
**Actions available**:
- **Increase position**: Add to existing position
- **Reduce position**: Partially close position
- **Set stop-loss**: Limit downside risk
- **Take profit order**: Lock in gains
- **Hedge**: Open opposite position in spot markets

#### Step 12: Position Closing
**Action**: Exit the trade
- Navigate to open position
- Click "Close" button
- Choose:
  - **Full close**: Close entire position
  - **Partial close**: Close specific amount
- Review closing price and fees
- Confirm transaction
- **Result**: P&L settled to account balance

#### Step 13: Settlement & Analysis
**Action**: Review trade performance
- Check "History" tab for trade details
- Settle unrealized P&L if needed
- Analyze:
  - Total return on investment
  - Fees paid (trading + funding)
  - Time in position
  - Learning points for future trades

---

### Post-Journey Actions

#### Ongoing Management
- Monitor remaining positions
- Manage collateral ratios
- Explore advanced features:
  - Subaccounts for strategy separation
  - Advanced order types
  - Cross-margin optimization

#### Knowledge Building
- Review Drift documentation for advanced features
- Join Discord community for market insights
- Practice with smaller positions before scaling up

---

## User Journey Flow 2: Providing Liquidity via Backstop AMM Liquidity (BAL)

### Pre-Journey Requirements
- User understands impermanent loss concepts
- User has significant capital to deploy ($1000+ recommended)
- User comfortable with advanced DeFi risks
- Existing Drift account (from Journey 1 or similar setup)

### Journey Overview
**Goal**: Become a liquidity provider earning yield through BAL participation
**User Type**: Advanced DeFi user with LP experience
**Duration**: 20-40 minutes (initial setup and research)

---

### Phase 1: Research & Preparation (10-15 minutes)

#### Step 1: Understanding BAL Mechanism
**Action**: Learn the system
- Read BAL documentation on docs.drift.trade
- Understand key concepts:
  - **BAL Shares**: Represent stake in AMM liquidity
  - **Pro-rata positions**: Share AMM's directional exposure
  - **K-adjustment**: How liquidity depth changes
  - **Revenue sharing**: Earn from trading fees
- **Risk factors**:
  - Directional exposure to market movements
  - Potential liquidation risk
  - Smart contract risk

#### Step 2: Market Selection & Analysis
**Action**: Choose optimal market for LP
- Analyze available BAL markets
- Review metrics for each:
  - Current BAL TVL and providers
  - Trading volume and fee generation
  - Market volatility and trends
  - Funding rate patterns
- Consider correlation with existing portfolio
- **Strategy**: Choose markets with consistent volume

#### Step 3: Capital Planning
**Action**: Determine LP allocation
- Calculate optimal position size
- Consider:
  - Risk tolerance for directional exposure
  - Diversification across multiple BAL markets
  - Liquidity needs (exit timeframes)
  - Expected APY vs other yield opportunities
- **Best practice**: Start with smaller allocation to test

---

### Phase 2: BAL Position Setup (5-10 minutes)

#### Step 4: Access BAL Interface
**Action**: Navigate to liquidity provision
- Go to app.drift.trade
- Navigate to "Earn" section
- Select "Backstop AMM Liquidity (BAL)"
- Review available markets and current yields
- Click on chosen market for detailed view

#### Step 5: Position Calculation
**Action**: Determine LP parameters
- Review current AMM state:
  - K-value (liquidity depth)
  - Current base/quote asset reserves
  - Mark price vs oracle price
  - Existing BAL provider count
- Calculate:
  - Required collateral for desired LP size
  - Resulting BAL share percentage
  - Expected directional exposure
  - Estimated yield based on recent fee generation

#### Step 6: BAL Share Acquisition
**Action**: Provide liquidity to AMM
- Specify LP amount (in USD terms)
- Review transaction details:
  - BAL shares to be received
  - Pro-rata position that will be assigned
  - Entry mark price
  - Expected trading fees
- **Important**: Understand you'll inherit AMM's current directional bias
- Confirm transaction and sign in wallet

---

### Phase 3: Active Management (Ongoing)

#### Step 7: Position Monitoring
**Action**: Track BAL performance
- Monitor in "Positions" tab:
  - BAL share value changes
  - Assigned perpetual position P&L
  - Fee earnings accumulation
  - Share of total AMM k-value
- Track metrics:
  - Total return (fees + position P&L)
  - APY calculation based on time in position
  - Market share percentage

#### Step 8: Risk Management
**Action**: Manage exposure and risks
- Monitor account health
- Watch for:
  - Large directional moves affecting position
  - Changes in market volatility
  - AMM rebalancing events
  - K-adjustments affecting share value
- **Risk controls**:
  - Set alerts for position size thresholds
  - Consider hedging directional exposure externally
  - Plan exit strategies for different scenarios

#### Step 9: Optimization Strategies
**Action**: Maximize LP efficiency
- **Rebalancing**: Adjust BAL allocations based on:
  - Relative fee generation across markets
  - Changing market conditions
  - Risk-adjusted return opportunities
- **Compounding**: Reinvest earned fees into BAL shares
- **Diversification**: Spread across multiple markets
- **Timing**: Monitor market cycles for optimal entry/exit

---

### Phase 4: Advanced Strategies (For Experienced Users)

#### Step 10: Delta-Neutral Strategies
**Action**: Hedge directional exposure
- Calculate current directional exposure from BAL position
- Open offsetting positions in:
  - Spot markets (opposite direction)
  - Other perpetual markets
  - External exchanges for larger hedges
- **Goal**: Isolate fee-earning component from price movements

#### Step 11: Cross-Strategy Integration
**Action**: Combine with other Drift products
- **Lending**: Lend unused collateral for additional yield
- **Insurance Fund Staking**: Diversify yield sources
- **Market Making**: Participate in JIT auctions for additional fees
- **Subaccounts**: Separate strategies for better risk management

#### Step 12: Performance Analysis
**Action**: Evaluate strategy effectiveness
- Track key metrics:
  - Fee APY vs initial projections
  - Impermanent loss/gain from directional exposure
  - Total return vs passive holding strategies
  - Risk-adjusted returns (Sharpe ratio)
- Compare with alternatives:
  - Simple lending yields
  - External LP opportunities
  - Traditional market making

---

### Phase 5: Exit Strategy (Variable Timing)

#### Step 13: Exit Planning
**Action**: Determine optimal exit conditions
- Monitor for exit signals:
  - Declining fee generation
  - Unfavorable market conditions
  - Better opportunities elsewhere
  - Risk management requirements
- **Timing considerations**:
  - Market volatility periods
  - Funding rate cycles
  - Personal liquidity needs

#### Step 14: BAL Share Redemption
**Action**: Exit LP position
- Navigate to BAL position in interface
- Select "Withdraw" or "Reduce Position"
- Specify amount to withdraw (partial or full)
- Review exit terms:
  - Current BAL share value
  - Position P&L settlement
  - Accumulated fee rewards
  - Total return calculation
- Confirm transaction and sign

#### Step 15: Final Settlement
**Action**: Complete exit process
- Verify all positions are closed
- Claim any remaining fee rewards
- Settle any unsettled P&L
- **Optional**: Withdraw funds to external wallet
- Document performance for tax reporting

---

### Post-Journey Optimization

#### Performance Review
- Calculate total returns including:
  - Fee income earned
  - Position P&L from directional exposure
  - Opportunity cost vs alternatives
- Identify lessons learned for future LP strategies

#### Strategy Refinement
- Adjust approach based on experience:
  - Optimal market selection criteria
  - Position sizing methodology
  - Risk management improvements
  - Integration with broader DeFi strategy

#### Community Engagement
- Share experiences with Drift community
- Stay updated on protocol improvements
- Participate in governance decisions affecting BAL mechanics

---

## Key Success Factors for Both Journeys

### Technical Requirements
1. **Stable internet connection** for real-time trading
2. **Adequate SOL balance** for transaction fees
3. **Wallet security** best practices
4. **Regular monitoring** capabilities

### Risk Management
1. **Position sizing** appropriate to risk tolerance
2. **Diversification** across strategies and timeframes
3. **Stop-loss disciplines** for trading
4. **Liquidity management** for LP positions

### Knowledge Building
1. **Continuous learning** about protocol updates
2. **Market analysis** skills development
3. **Community engagement** for insights
4. **Documentation review** for new features

### Long-term Success
1. **Strategy evolution** based on experience
2. **Risk-adjusted return** optimization
3. **Portfolio integration** with broader DeFi activities
4. **Tax planning** and record keeping

---

*These user journeys are based on official Drift Protocol documentation as of January 2025. Always refer to the latest documentation at docs.drift.trade for the most current information and features.*