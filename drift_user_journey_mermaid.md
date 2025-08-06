# Drift Protocol User Journey Flows - Mermaid Implementation

## Journey 1: Perpetual Trading Flow

```mermaid
flowchart TD
    Start([New User Wants to Trade Perps]) --> WalletCheck{Has Solana Wallet?}
    
    WalletCheck -->|No| CreateWallet[Create Phantom Wallet<br/>- Download extension<br/>- Secure seed phrase]
    WalletCheck -->|Yes| CheckSOL{Has SOL for fees?}
    
    CreateWallet --> GetSOL[Get SOL<br/>- Buy on CEX<br/>- Withdraw to wallet]
    CheckSOL -->|No| GetSOL
    CheckSOL -->|Yes| ConnectDrift[Connect to app.drift.trade]
    
    GetSOL --> ConnectDrift
    ConnectDrift --> WalletConnect[Connect Wallet<br/>- Sign message<br/>- Pay 0.035 SOL setup]
    
    WalletConnect --> Deposit[Deposit Collateral<br/>- USDC recommended<br/>- Min $100-500]
    Deposit --> CheckBalance[Verify Account Balance<br/>& Free Collateral]
    
    CheckBalance --> SelectMarket[Choose Perp Market<br/>- SOL-PERP popular<br/>- Analyze volume & funding]
    SelectMarket --> PlanTrade[Plan Trade<br/>- Direction: Long/Short<br/>- Position size<br/>- Leverage 1x-101x]
    
    PlanTrade --> OrderType{Select Order Type}
    OrderType -->|Market| PlaceMarket[Market Order<br/>- Immediate execution<br/>- Set size & leverage]
    OrderType -->|Limit| PlaceLimit[Limit Order<br/>- Set price target<br/>- Set size & leverage]
    OrderType -->|Advanced| PlaceAdvanced[Stop Loss/Take Profit<br/>- Risk management]
    
    PlaceMarket --> ReviewOrder[Review Trade Summary<br/>- Entry price<br/>- Fees ~0.1%<br/>- Margin required]
    PlaceLimit --> ReviewOrder
    PlaceAdvanced --> ReviewOrder
    
    ReviewOrder --> ConfirmTrade[Confirm Transaction]
    ConfirmTrade --> JITAuction[5-Second JIT Auction<br/>Market makers compete]
    
    JITAuction --> ExecutionPath{Execution Route}
    ExecutionPath -->|JIT Fill| JITFill[Filled by Market Maker<br/>Better price]
    ExecutionPath -->|DLOB Match| DLOBFill[Matched with Limit Order]
    ExecutionPath -->|AMM Fill| AMMFill[Filled against AMM<br/>Guaranteed liquidity]
    
    JITFill --> MonitorPosition[Position Active<br/>Monitor in Positions tab]
    DLOBFill --> MonitorPosition
    AMMFill --> MonitorPosition
    
    MonitorPosition --> TrackMetrics[Track Real-time<br/>- Unrealized P&L<br/>- Funding payments<br/>- Account health]
    
    TrackMetrics --> ManagePosition{Manage Position?}
    ManagePosition -->|Adjust| AdjustOptions[- Increase size<br/>- Reduce size<br/>- Set stop-loss<br/>- Take profit]
    ManagePosition -->|Hold| ContinueMonitor[Continue Monitoring]
    ManagePosition -->|Close| ClosePosition[Close Position<br/>- Full or partial<br/>- Review exit price]
    
    AdjustOptions --> TrackMetrics
    ContinueMonitor --> TrackMetrics
    ClosePosition --> SettlePNL[Settle P&L<br/>Update account balance]
    
    SettlePNL --> AnalyzePerformance[Analyze Trade<br/>- Total return<br/>- Fees paid<br/>- Learning points]
    AnalyzePerformance --> Complete([Trading Journey Complete])
    
    style Start fill:#e3f2fd
    style Complete fill:#c8e6c9
    style JITAuction fill:#fff3e0
    style ExecutionPath fill:#f3e5f5
```

## Journey 2: Liquidity Provision (BAL) Flow

```mermaid
flowchart TD
    Start([Advanced User - Provide Liquidity]) --> Prerequisites{Ready for BAL?}
    
    Prerequisites -->|No| Learn[Learn Requirements<br/>- Drift account needed<br/>- Understand impermanent loss<br/>- $1000+ recommended]
    Prerequisites -->|Yes| Research[Research BAL Mechanism<br/>- Read documentation<br/>- Understand risks]
    
    Learn --> Research
    Research --> MarketAnalysis[Analyze BAL Markets<br/>- TVL & volume<br/>- Fee generation<br/>- Volatility patterns]
    
    MarketAnalysis --> PlanCapital[Plan Capital Allocation<br/>- Risk tolerance<br/>- Diversification needs<br/>- Expected returns]
    
    PlanCapital --> AccessInterface[Navigate to Drift App<br/>Go to Earn → BAL]
    AccessInterface --> SelectMarket[Choose BAL Market<br/>Review yields & metrics]
    
    SelectMarket --> CalculatePosition[Calculate LP Parameters<br/>- Required collateral<br/>- BAL share %<br/>- Directional exposure]
    
    CalculatePosition --> ReviewTerms[Review Transaction<br/>- BAL shares received<br/>- Pro-rata position<br/>- Expected fees]
    
    ReviewTerms --> UnderstandRisk[⚠️ Critical Understanding<br/>You inherit AMM's<br/>directional bias]
    UnderstandRisk --> ConfirmLP[Confirm LP Transaction]
    
    ConfirmLP --> ActivePosition[BAL Position Active<br/>Monitor performance]
    
    ActivePosition --> TrackPerformance[Track Metrics<br/>- Share value<br/>- Fee earnings<br/>- Position P&L<br/>- APY calculation]
    
    TrackPerformance --> RiskCheck{Risk Management?}
    RiskCheck -->|Needed| RiskActions[Risk Controls<br/>- Set alerts<br/>- Consider hedging<br/>- Plan exit strategy]
    RiskCheck -->|Stable| Optimize[Optimization<br/>- Rebalance allocations<br/>- Compound returns<br/>- Diversify markets]
    
    RiskActions --> ContinueMonitoring[Continue Monitoring]
    Optimize --> AdvancedStrategy{Advanced Strategies?}
    
    AdvancedStrategy -->|Yes| DeltaNeutral[Delta-Neutral Hedging<br/>- Calculate exposure<br/>- Open offsetting positions<br/>- Isolate fee income]
    AdvancedStrategy -->|No| ContinueMonitoring
    
    DeltaNeutral --> CrossStrategy[Cross-Strategy Integration<br/>- Lending unused collateral<br/>- Insurance fund staking<br/>- JIT market making]
    
    CrossStrategy --> PerformanceAnalysis[Performance Analysis<br/>- Fee APY vs projections<br/>- Risk-adjusted returns<br/>- Compare alternatives]
    
    PerformanceAnalysis --> ContinueMonitoring
    ContinueMonitoring --> ExitDecision{Time to Exit?}
    
    ExitDecision -->|No| TrackPerformance
    ExitDecision -->|Yes| PlanExit[Plan Exit Strategy<br/>- Monitor exit signals<br/>- Consider timing<br/>- Market conditions]
    
    PlanExit --> ExecuteExit[Execute Exit<br/>- Navigate to position<br/>- Select withdraw amount<br/>- Review exit terms]
    
    ExecuteExit --> FinalSettlement[Final Settlement<br/>- Close positions<br/>- Claim fees<br/>- Settle P&L]
    
    FinalSettlement --> DocumentResults[Document Performance<br/>- Calculate returns<br/>- Tax reporting<br/>- Strategy refinement]
    
    DocumentResults --> Complete([BAL Journey Complete])
    
    style Start fill:#e3f2fd
    style Complete fill:#c8e6c9
    style UnderstandRisk fill:#ffebee
    style RiskCheck fill:#fff3e0
    style AdvancedStrategy fill:#f3e5f5
```

## User Type Decision Flow

```mermaid
flowchart TD
    Entry([User Discovers Drift]) --> Experience{Experience Level?}
    
    Experience -->|New to DeFi| Learn[Learn DeFi Basics First<br/>- Wallet security<br/>- Risk understanding<br/>- Start small]
    Experience -->|Some Crypto| Assessment[Quick Assessment<br/>- Capital available?<br/>- Risk tolerance?<br/>- Time commitment?]
    Experience -->|DeFi Experienced| AdvancedPath[Advanced Options<br/>- Multiple strategies<br/>- Higher capital<br/>- Complex risk management]
    
    Learn --> BeginnerSetup[Beginner-Friendly Setup<br/>- Start with $100-500<br/>- Low leverage 2x-5x<br/>- Focus on learning]
    
    Assessment --> Capital{Capital Amount?}
    Capital -->|$100-$1000| IntermediateTrading[Intermediate Trading<br/>Journey 1: Perp Trading<br/>Conservative approach]
    Capital -->|$1000+| RiskChoice{Risk Preference?}
    
    RiskChoice -->|Conservative| LendingFocus[Lending + Light Trading<br/>Gradual skill building]
    RiskChoice -->|Moderate| BalancedApproach[Trading + Insurance Staking<br/>Diversified strategy]
    RiskChoice -->|Aggressive| HighYieldPath[BAL + Advanced Trading<br/>Journey 2: Liquidity Provision]
    
    AdvancedPath --> MultiStrategy[Multi-Strategy Approach<br/>- Combine trading & LP<br/>- Delta-neutral strategies<br/>- Portfolio optimization]
    
    BeginnerSetup --> Journey1[Execute Journey 1<br/>Perpetual Trading]
    IntermediateTrading --> Journey1
    LendingFocus --> ConservativeStart[Start Conservative<br/>Build experience gradually]
    BalancedApproach --> Journey1
    HighYieldPath --> Journey2[Execute Journey 2<br/>BAL Liquidity Provision]
    MultiStrategy --> BothJourneys[Execute Both Journeys<br/>Integrated approach]
    
    Journey1 --> Success1{Successful Trading?}
    Success1 -->|Yes| Expand[Expand to Other Features<br/>- Larger positions<br/>- Advanced orders<br/>- Yield strategies]
    Success1 -->|No| Refine[Refine Approach<br/>- Reduce size<br/>- Learn more<br/>- Practice patience]
    
    Journey2 --> Success2{Successful LP?}
    Success2 -->|Yes| Advanced[Advanced LP Strategies<br/>- Multi-market<br/>- Delta-neutral<br/>- Cross-collateral optimization]
    Success2 -->|No| Reassess[Reassess Strategy<br/>- Risk management<br/>- Market selection<br/>- Position sizing]
    
    ConservativeStart --> GradualProgress[Gradual Progression<br/>Build confidence & capital]
    BothJourneys --> PowerUser[Drift Power User<br/>Advanced portfolio management]
    
    Refine --> Journey1
    Expand --> Consider2{Consider BAL?}
    Consider2 -->|Yes| Journey2
    Consider2 -->|No| MasterTrading[Master Trading First]
    
    Reassess --> Journey2
    Advanced --> PowerUser
    GradualProgress --> Expand
    MasterTrading --> PowerUser
    
    style Entry fill:#e3f2fd
    style PowerUser fill:#c8e6c9
    style Learn fill:#fff3e0
    style Assessment fill:#f3e5f5
```

## Risk Management Flow

```mermaid
flowchart TD
    Monitor([Regular Account Monitoring]) --> HealthCheck{Account Health?}
    
    HealthCheck -->|Healthy 50%+| Normal[✅ Normal Operations<br/>Continue strategy]
    HealthCheck -->|Warning 20-50%| Alert[⚠️ Risk Alert<br/>Take precautions]
    HealthCheck -->|Critical <20%| Emergency[🚨 Emergency Action<br/>Immediate response needed]
    
    Alert --> AlertActions[Risk Management Actions<br/>- Reduce position sizes<br/>- Add collateral<br/>- Set stop losses<br/>- Monitor closely]
    
    Emergency --> EmergencyChoice{Emergency Options}
    EmergencyChoice -->|Close Positions| QuickClose[Close Positions Immediately<br/>Prevent liquidation]
    EmergencyChoice -->|Add Funds| FastDeposit[Deposit Funds Fast<br/>Restore health ratio]
    EmergencyChoice -->|Partial Exit| PartialClose[Partial Position Closure<br/>Reduce risk exposure]
    
    Normal --> ContinueStrategy[Continue Current Strategy<br/>Regular monitoring]
    AlertActions --> MonitorImprovement[Monitor for Improvement<br/>Adjust as needed]
    QuickClose --> Stabilize[Stabilize Account<br/>Reassess strategy]
    FastDeposit --> RestoreHealth[Health Restored<br/>Resume careful operations]
    PartialClose --> ReducedRisk[Risk Reduced<br/>Monitor recovery]
    
    ContinueStrategy --> RegularCheck[Regular Health Checks<br/>Proactive monitoring]
    MonitorImprovement --> Recovered{Recovery Status?}
    Recovered -->|Improved| BackToNormal[Return to Normal Ops<br/>Lessons learned]
    Recovered -->|Still at Risk| MaintainCaution[Maintain Caution<br/>Conservative approach]
    
    Stabilize --> LearnFromExperience[Learn from Experience<br/>Improve risk management]
    RestoreHealth --> ImprovedPractices[Improved Practices<br/>Better risk controls]
    ReducedRisk --> GradualRecovery[Gradual Recovery<br/>Rebuild confidence]
    
    BackToNormal --> RegularCheck
    MaintainCaution --> AlertActions
    LearnFromExperience --> BetterRiskManagement[Better Risk Management<br/>Enhanced strategy]
    ImprovedPractices --> BetterRiskManagement
    GradualRecovery --> BetterRiskManagement
    
    RegularCheck --> Monitor
    BetterRiskManagement --> Monitor
    
    style Monitor fill:#e3f2fd
    style Normal fill:#c8e6c9
    style Alert fill:#ffeb3b
    style Emergency fill:#f44336
    style BetterRiskManagement fill:#4caf50
```

## Integration & Progression Flow

```mermaid
flowchart LR
    Trading[Journey 1<br/>Perp Trading<br/>💹] --> TradingResults{Trading Success?}
    LP[Journey 2<br/>BAL Provision<br/>💧] --> LPResults{LP Success?}
    
    TradingResults -->|Profitable| TradingProfits[Trading Profits<br/>Excess collateral]
    TradingResults -->|Learning| TradingExp[Trading Experience<br/>Market knowledge]
    
    LPResults -->|Profitable| LPIncome[LP Fee Income<br/>Steady yield]
    LPResults -->|Learning| LPExp[LP Experience<br/>Risk management]
    
    TradingProfits --> Integration[💡 Integration Opportunities]
    TradingExp --> Integration
    LPIncome --> Integration
    LPExp --> Integration
    
    Integration --> CrossCollateral[Cross-Collateral Optimization<br/>Use trading profits for LP]
    Integration --> DeltaNeutral[Delta-Neutral Strategies<br/>Hedge LP exposure with perps]
    Integration --> YieldMax[Yield Maximization<br/>Compound across strategies]
    Integration --> RiskDiv[Risk Diversification<br/>Multiple income streams]
    
    CrossCollateral --> Advanced[Advanced Portfolio<br/>Management 🎯]
    DeltaNeutral --> Advanced
    YieldMax --> Advanced
    RiskDiv --> Advanced
    
    Advanced --> Monitoring[Continuous Monitoring<br/>& Optimization]
    Monitoring --> Scaling[Scale Successful<br/>Strategies]
    Scaling --> PowerUser[Drift Protocol<br/>Power User 🚀]
    
    PowerUser --> Community[Community Contribution<br/>- Share strategies<br/>- Mentor others<br/>- Protocol governance]
    
    style Trading fill:#e3f2fd
    style LP fill:#f3e5f5
    style Integration fill:#fff3e0
    style Advanced fill:#e8f5e8
    style PowerUser fill:#c8e6c9
    style Community fill:#f0f4c3
```

## Quick Start Decision Tree

```mermaid
flowchart TD
    Start([Want to Start with Drift?]) --> Ready{Ready to Begin?}
    
    Ready -->|Not Ready| Prepare[📚 Preparation Needed<br/>- Learn wallet basics<br/>- Understand risks<br/>- Get SOL for fees]
    Ready -->|Ready| QuickAssess[⚡ Quick Assessment]
    
    QuickAssess --> Time{Time Available?}
    Time -->|Limited| SimpleStart[🎯 Simple Start<br/>- Small trading position<br/>- Learn interface<br/>- Low risk]
    Time -->|Flexible| FullJourney[🚀 Full Journey<br/>- Complete setup<br/>- Multiple strategies<br/>- Comprehensive approach]
    
    SimpleStart --> SmallTrade[Start Small Trade<br/>$100-200 position<br/>2x leverage max]
    FullJourney --> ChooseJourney{Primary Interest?}
    
    ChooseJourney -->|Trading Focus| TradingPath[📈 Trading Path<br/>Journey 1: Perps]
    ChooseJourney -->|Yield Focus| YieldPath[💰 Yield Path<br/>Journey 2: BAL]
    ChooseJourney -->|Both| ComprehensivePath[🎯 Comprehensive<br/>Both journeys]
    
    SmallTrade --> Experience[Gain Experience<br/>Learn platform]
    TradingPath --> ExecuteTrading[Execute Trading Journey]
    YieldPath --> ExecuteLP[Execute LP Journey]
    ComprehensivePath --> ExecuteBoth[Execute Both Journeys]
    
    Experience --> Expand{Want to Expand?}
    Expand -->|Yes| ChooseJourney
    Expand -->|No| StaySimple[Stay Simple<br/>Perfect current approach]
    
    ExecuteTrading --> TradingSuccess[Trading Success<br/>Consider adding LP]
    ExecuteLP --> LPSuccess[LP Success<br/>Consider adding trading]
    ExecuteBoth --> IntegratedSuccess[Integrated Success<br/>Advanced strategies]
    
    StaySimple --> Mastery[Master Simple Approach]
    TradingSuccess --> Consider[Consider Integration]
    LPSuccess --> Consider
    IntegratedSuccess --> ExpertLevel[Expert Level User]
    
    Mastery --> Success[🎉 Success with Drift]
    Consider --> Success
    ExpertLevel --> Success
    
    Prepare --> Ready
    
    style Start fill:#e3f2fd
    style Success fill:#c8e6c9
    style Prepare fill:#fff3e0
    style SimpleStart fill:#e8f5e8
    style FullJourney fill:#f3e5f5
```

---

## Implementation Notes

### Using These Charts:
1. **Copy any chart** and paste into Mermaid Live Editor (mermaid.live)
2. **Integrate into docs** - Works with GitHub, GitLab, Notion, Confluence
3. **Customize styling** - Modify colors, shapes, or text as needed
4. **Link between charts** - Reference other journeys in documentation

### Color Coding:
- 🟦 **Light Blue** (`#e3f2fd`): Start points, entry
- 🟩 **Light Green** (`#c8e6c9`): Success, completion
- 🟨 **Light Yellow** (`#fff3e0`): Important decisions, warnings
- 🟪 **Light Purple** (`#f3e5f5`): Advanced features, optional paths
- 🟥 **Light Red** (`#ffebee`): Critical warnings, high risk

### Best Practices:
- Start with the **Quick Start Decision Tree** for new users
- Use **Risk Management Flow** for safety education
- Reference **Integration Flow** for advanced users
- Keep charts focused - one main concept per diagram