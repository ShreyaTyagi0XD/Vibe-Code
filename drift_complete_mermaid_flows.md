# Drift Protocol Complete User Journey Flows - Advanced Features

Based on official documentation from https://docs.drift.trade/

---

## Complete Onboarding Flow with Advanced Features

```mermaid
flowchart TD
    Start([User Visits app.drift.trade]) --> LoginChoice{Choose Authentication Method}
    
    LoginChoice -->|Fastest & Easiest| SocialLogin[🔐 Passwordless Social Login<br/>- Email verification<br/>- Google/Apple/Discord<br/>- Auto-wallet creation<br/>- No seed phrase needed]
    
    LoginChoice -->|Recommended| Phantom[🦄 Phantom Wallet<br/>- Native Solana support<br/>- Auto-confirm feature<br/>- Mobile & desktop<br/>- Built-in DEX integration]
    
    LoginChoice -->|Multi-chain Users| MetaMask[🦊 MetaMask Setup<br/>- Install extension<br/>- Add Solana network<br/>- Configure RPC endpoints<br/>- Multi-chain portfolio]
    
    LoginChoice -->|Maximum Security| Hardware[🔒 Hardware Wallet<br/>- Ledger + Phantom<br/>- Cold storage security<br/>- Transaction signing<br/>- Enterprise-grade protection]
    
    LoginChoice -->|Other Options| AlternativeWallets[⚙️ 20+ Other Wallets<br/>- Solflare<br/>- Glow<br/>- Backpack<br/>- Coinbase Wallet<br/>- And more...]
    
    SocialLogin --> SocialSetup[📧 Social Authentication<br/>1. Choose provider<br/>2. Verify identity<br/>3. Generate Magic Wallet<br/>4. Secure private key<br/>5. Email recovery setup]
    
    Phantom --> PhantomFlow[🦄 Phantom Connection<br/>1. Install/connect<br/>2. Auto-confirm setup<br/>3. Connected apps management<br/>4. One-click transactions]
    
    MetaMask --> MetaMaskSetup[🦊 MetaMask Configuration<br/>1. Install MetaMask<br/>2. Add Solana Network<br/>3. Configure RPC<br/>4. Test connection<br/>5. Multi-chain switching]
    
    Hardware --> HardwareSetup[🔒 Hardware Integration<br/>1. Set up Ledger device<br/>2. Install Solana app<br/>3. Connect to Phantom<br/>4. Verify security<br/>5. Transaction approval flow]
    
    AlternativeWallets --> WalletSpecific[🔧 Wallet-Specific Setup<br/>Follow individual<br/>wallet instructions]
    
    SocialSetup --> FundingOptions{Choose Funding Method}
    PhantomFlow --> FundingOptions
    MetaMaskSetup --> FundingOptions
    HardwareSetup --> FundingOptions
    WalletSpecific --> FundingOptions
    
    FundingOptions -->|Credit Card| FiatOnRamp[💳 Direct Purchase<br/>- Buy USDC/SOL directly<br/>- Integrated providers<br/>- Instant availability<br/>- KYC verification]
    
    FundingOptions -->|Crypto Transfer| CryptoDeposit[₿ Crypto Deposit<br/>- From exchanges<br/>- From other wallets<br/>- Cross-chain bridges<br/>- Network verification]
    
    FundingOptions -->|CEX Withdrawal| CEXTransfer[🏦 Exchange Withdrawal<br/>- Binance/Coinbase/Kraken<br/>- Solana network selection<br/>- Address verification<br/>- Withdrawal limits]
    
    FiatOnRamp --> AccountInit[🚀 Account Initialization<br/>- Pay 0.035 SOL setup fee<br/>- Create main subaccount<br/>- Enable versioned transactions<br/>- Security preferences]
    CryptoDeposit --> AccountInit
    CEXTransfer --> AccountInit
    
    AccountInit --> SubaccountSetup[📁 Subaccount Management<br/>Setup multiple trading strategies]
    
    SubaccountSetup --> SubaccountChoice{Subaccount Strategy?}
    SubaccountChoice -->|Simple| SingleAccount[Single Main Account<br/>- All-in-one trading<br/>- Beginner-friendly<br/>- Unified P&L tracking]
    
    SubaccountChoice -->|Advanced| MultipleAccounts[Multiple Subaccounts<br/>- Strategy separation<br/>- Risk isolation<br/>- Professional trading]
    
    SingleAccount --> TradingReady[✅ Ready to Trade<br/>All features available]
    
    MultipleAccounts --> SubaccountFeatures[🔧 Advanced Subaccount Features<br/>- Create named subaccounts<br/>- Set individual risk limits<br/>- Transfer between accounts<br/>- Delegate account access<br/>- Cross-collateral optimization]
    
    SubaccountFeatures --> DelegateChoice{Need Delegation?}
    DelegateChoice -->|No| TradingReady
    DelegateChoice -->|Yes| DelegateSetup[👥 Delegated Account Setup<br/>- Add delegate authority<br/>- Set permissions<br/>- Trading on behalf<br/>- Institutional features]
    
    DelegateSetup --> TradingReady
    
    style Start fill:#e3f2fd
    style TradingReady fill:#c8e6c9
    style SocialLogin fill:#e8f5e8
    style MetaMask fill:#ffa500
    style Hardware fill:#ffecb3
    style MultipleAccounts fill:#f3e5f5
    style DelegateSetup fill:#fff3e0
```

## MetaMask Detailed Setup Flow

```mermaid
flowchart TD
    MetaMaskStart([MetaMask Setup for Drift]) --> HasMetaMask{MetaMask Installed?}
    
    HasMetaMask -->|No| InstallMM[📥 Install MetaMask<br/>1. Visit metamask.io<br/>2. Download extension<br/>3. Create/import wallet<br/>4. Secure seed phrase<br/>5. Set strong password]
    
    HasMetaMask -->|Yes| CheckSolana{Solana Network Added?}
    
    InstallMM --> CheckSolana
    
    CheckSolana -->|No| AddSolanaNetwork[🌐 Add Solana Network<br/>Manual configuration required]
    CheckSolana -->|Yes| TestConnection[🔌 Test Connection<br/>Verify Solana functionality]
    
    AddSolanaNetwork --> NetworkConfig[⚙️ Solana Network Configuration<br/>Network Name: Solana Mainnet<br/>RPC URL: https://api.mainnet-beta.solana.com<br/>Chain ID: Leave blank<br/>Symbol: SOL<br/>Block Explorer: https://solscan.io]
    
    NetworkConfig --> SaveNetwork[💾 Save Network Configuration<br/>- Add to MetaMask<br/>- Test connectivity<br/>- Verify SOL balance display]
    
    SaveNetwork --> TestConnection
    
    TestConnection --> ConnectionResult{Connection Status?}
    ConnectionResult -->|Success| MetaMaskReady[✅ MetaMask Ready for Drift<br/>- Solana network active<br/>- SOL balance visible<br/>- Ready to connect]
    
    ConnectionResult -->|Failed| TroubleshootMM[🔧 Troubleshoot Connection<br/>- Check RPC URL<br/>- Verify network settings<br/>- Try alternative RPC<br/>- Contact support if needed]
    
    TroubleshootMM --> NetworkConfig
    
    MetaMaskReady --> ConnectToDrift[🚀 Connect to Drift<br/>1. Visit app.drift.trade<br/>2. Click Connect Wallet<br/>3. Select MetaMask<br/>4. Approve connection<br/>5. Switch to Solana network]
    
    ConnectToDrift --> MMFeatures[🦊 MetaMask Features<br/>✅ Multi-chain portfolio view<br/>✅ Hardware wallet support<br/>✅ Mobile app sync<br/>✅ DApp ecosystem access<br/>⚠️ Manual Solana setup<br/>⚠️ Network switching needed]
    
    MMFeatures --> FundingMM[💰 Funding MetaMask for Drift<br/>Multiple options available]
    
    FundingMM --> FundingMethodMM{Choose Funding Method}
    FundingMethodMM -->|Cross-chain| BridgeToSolana[🌉 Bridge to Solana<br/>- From Ethereum/Polygon<br/>- Use Wormhole/Portal<br/>- Cross-chain swaps<br/>- Bridge fees apply]
    
    FundingMethodMM -->|Direct Purchase| BuySOL[💳 Buy SOL Direct<br/>- In-wallet purchase<br/>- Credit card/bank<br/>- Instant availability<br/>- Higher fees]
    
    FundingMethodMM -->|CEX Transfer| CEXToMM[🏦 CEX to MetaMask<br/>- Withdraw from exchange<br/>- Select Solana network<br/>- Verify address<br/>- Lower fees]
    
    BridgeToSolana --> MMComplete[🎉 MetaMask Setup Complete<br/>Ready for Drift trading]
    BuySOL --> MMComplete
    CEXToMM --> MMComplete
    
    style MetaMaskStart fill:#e3f2fd
    style MMComplete fill:#c8e6c9
    style AddSolanaNetwork fill:#fff3e0
    style TroubleshootMM fill:#ffebee
    style MMFeatures fill:#ffa500
```

## Passwordless Social Login Flow

```mermaid
flowchart TD
    SocialStart([Choose Social Login]) --> ProviderSelect{Select Authentication Provider}
    
    ProviderSelect -->|Universal| EmailAuth[📧 Email Authentication<br/>Most compatible option]
    ProviderSelect -->|Fast| GoogleAuth[🔍 Google OAuth<br/>One-click authentication]
    ProviderSelect -->|Privacy| AppleAuth[🍎 Apple ID<br/>Privacy-focused signin]
    ProviderSelect -->|Crypto Native| DiscordAuth[💬 Discord<br/>Crypto community integration]
    ProviderSelect -->|Social| TwitterAuth[🐦 Twitter/X<br/>Social verification]
    ProviderSelect -->|Developer| GitHubAuth[⚡ GitHub<br/>Developer community]
    
    EmailAuth --> EmailFlow[📧 Email Verification Process<br/>1. Enter email address<br/>2. Receive verification code<br/>3. Enter 6-digit code<br/>4. Set optional password<br/>5. Magic Wallet created]
    
    GoogleAuth --> GoogleFlow[🔍 Google OAuth Process<br/>1. Click 'Continue with Google'<br/>2. Select Google account<br/>3. Grant permissions<br/>4. Instant authentication<br/>5. Return to Drift]
    
    AppleAuth --> AppleFlow[🍎 Apple ID Process<br/>1. Click 'Sign in with Apple'<br/>2. Face ID/Touch ID/Password<br/>3. Privacy options<br/>4. Share/hide email<br/>5. Secure authentication]
    
    DiscordAuth --> DiscordFlow[💬 Discord Integration<br/>1. Authorize Discord app<br/>2. Select server permissions<br/>3. Verify account standing<br/>4. Community benefits<br/>5. Crypto-native features]
    
    TwitterAuth --> TwitterFlow[🐦 Twitter Verification<br/>1. Connect Twitter account<br/>2. Verify account activity<br/>3. Social proof validation<br/>4. Community features<br/>5. Enhanced trading features]
    
    GitHubAuth --> GitHubFlow[⚡ GitHub Developer Auth<br/>1. Authorize GitHub app<br/>2. Verify developer status<br/>3. Repository access<br/>4. Technical community<br/>5. Developer features]
    
    EmailFlow --> MagicWallet[🪄 Magic Wallet Creation<br/>Non-custodial wallet<br/>auto-generated securely]
    GoogleFlow --> MagicWallet
    AppleFlow --> MagicWallet
    DiscordFlow --> MagicWallet
    TwitterFlow --> MagicWallet
    GitHubFlow --> MagicWallet
    
    MagicWallet --> WalletFeatures[✨ Magic Wallet Features<br/>✅ Passwordless login<br/>✅ Email recovery<br/>✅ No seed phrase management<br/>✅ Multi-factor authentication<br/>✅ Biometric support<br/>✅ Social verification<br/>⚠️ Account service dependence]
    
    WalletFeatures --> SecuritySetup[🛡️ Security Configuration<br/>- Set up 2FA/MFA<br/>- Biometric authentication<br/>- Device management<br/>- Recovery email<br/>- Session controls]
    
    SecuritySetup --> PrivateKeyAccess[🔑 Private Key Management<br/>- View private key option<br/>- Export for other wallets<br/>- Secure backup methods<br/>- Recovery procedures<br/>- Security warnings]
    
    PrivateKeyAccess --> FundingSocial[💰 Funding Social Wallet<br/>Beginner-friendly options]
    
    FundingSocial --> FundingChoiceSocial{Choose Funding Method}
    FundingChoiceSocial -->|Easiest| CreditCardDirect[💳 Credit Card Purchase<br/>- Buy USDC/SOL directly<br/>- Instant availability<br/>- Integrated payment<br/>- KYC verification<br/>- Higher fees but convenient]
    
    FundingChoiceSocial -->|Bank Transfer| ACHTransfer[🏦 Bank Transfer<br/>- ACH/wire transfer<br/>- Lower fees<br/>- 1-3 day processing<br/>- Larger amounts<br/>- Bank verification]
    
    FundingChoiceSocial -->|Mobile Payment| MobilePayments[📱 Mobile Payments<br/>- Apple Pay/Google Pay<br/>- Touch/Face ID<br/>- Instant processing<br/>- Mobile-optimized<br/>- Platform integration]
    
    FundingChoiceSocial -->|Crypto Deposit| CryptoDeposit[₿ Crypto Transfer<br/>- From other wallets<br/>- From exchanges<br/>- Cross-chain bridges<br/>- Standard network fees]
    
    CreditCardDirect --> SocialComplete[🎉 Social Login Complete<br/>- No technical setup required<br/>- Familiar authentication<br/>- Easy fund management<br/>- Beginner-friendly DeFi<br/>- Ready to trade on Drift]
    ACHTransfer --> SocialComplete
    MobilePayments --> SocialComplete
    CryptoDeposit --> SocialComplete
    
    style SocialStart fill:#e3f2fd
    style SocialComplete fill:#c8e6c9
    style MagicWallet fill:#e1f5fe
    style EmailAuth fill:#e8f5e8
    style GoogleAuth fill:#ffeaa7
    style AppleAuth fill:#dda0dd
    style DiscordAuth fill:#b19cd9
    style WalletFeatures fill:#f0f4c3
```

## Advanced Subaccount Management Flow

```mermaid
flowchart TD
    SubaccountStart([Subaccount Management]) --> CurrentStatus{Current Setup?}
    
    CurrentStatus -->|Single Account| SingleUser[📱 Single Main Account<br/>- Simple setup<br/>- All-in-one trading<br/>- Unified P&L<br/>- Beginner-friendly]
    
    CurrentStatus -->|Multiple Accounts| MultiUser[📁 Multiple Subaccounts<br/>- Advanced setup<br/>- Strategy separation<br/>- Risk isolation<br/>- Professional trading]
    
    SingleUser --> UpgradeChoice{Want Advanced Features?}
    UpgradeChoice -->|No| SingleFeatures[🎯 Single Account Features<br/>- Trade all markets<br/>- Cross-collateral benefits<br/>- Simplified management<br/>- Easy P&L tracking]
    
    UpgradeChoice -->|Yes| CreateSubaccounts[➕ Create Additional Subaccounts<br/>Upgrade to advanced setup]
    
    MultiUser --> ManageSubaccounts[⚙️ Manage Existing Subaccounts<br/>Advanced account operations]
    CreateSubaccounts --> ManageSubaccounts
    
    ManageSubaccounts --> SubaccountOperations[🔧 Subaccount Operations Menu]
    
    SubaccountOperations --> CreateNew[➕ Create New Subaccount<br/>- Choose unique name<br/>- Set risk parameters<br/>- Define strategy purpose<br/>- Allocate initial funds]
    
    SubaccountOperations --> TransferFunds[💸 Transfer Between Subaccounts<br/>- Move collateral<br/>- Transfer positions<br/>- Optimize capital allocation<br/>- Risk management]
    
    SubaccountOperations --> SetDelegates[👥 Delegate Account Access<br/>- Add trusted parties<br/>- Set permissions<br/>- Trading authorization<br/>- Institutional features]
    
    SubaccountOperations --> ConfigureRisk[⚠️ Configure Risk Settings<br/>- Set margin ratios<br/>- Position limits<br/>- Stop-loss rules<br/>- Account-specific limits]
    
    SubaccountOperations --> MonitorPerformance[📊 Monitor Performance<br/>- Individual P&L tracking<br/>- Strategy analysis<br/>- Risk metrics<br/>- Comparative performance]
    
    CreateNew --> NameSubaccount[📝 Subaccount Configuration<br/>- Name: e.g., 'BTC Strategy'<br/>- Purpose: e.g., 'Long-term holds'<br/>- Risk level: Conservative/Aggressive<br/>- Initial funding amount]
    
    NameSubaccount --> FundSubaccount[💰 Fund New Subaccount<br/>- Transfer from main account<br/>- Deposit new funds<br/>- Set collateral allocation<br/>- Activate trading]
    
    TransferFunds --> TransferType{Transfer Type?}
    TransferType -->|Collateral| TransferCollateral[💎 Transfer Collateral<br/>- Choose source account<br/>- Select destination<br/>- Enter amount<br/>- Confirm transfer<br/>- Real-time execution]
    
    TransferType -->|Positions| TransferPositions[📈 Transfer Positions<br/>- Select open positions<br/>- Choose destination account<br/>- Transfer P&L<br/>- Update margin requirements<br/>- Strategy reallocation]
    
    SetDelegates --> DelegateSetup[👥 Delegate Configuration<br/>- Add delegate authority<br/>- Set permission levels<br/>- Define trading limits<br/>- Enable notifications<br/>- Audit trail setup]
    
    DelegateSetup --> DelegatePermissions[🔐 Delegate Permissions<br/>- Trading authorization<br/>- Withdrawal limits<br/>- Market access<br/>- Risk parameter changes<br/>- Reporting access]
    
    ConfigureRisk --> RiskParameters[⚠️ Risk Parameter Setup<br/>- Maximum leverage per account<br/>- Position size limits<br/>- Stop-loss requirements<br/>- Margin call thresholds<br/>- Emergency procedures]
    
    MonitorPerformance --> PerformanceMetrics[📊 Performance Analytics<br/>- Individual account P&L<br/>- Risk-adjusted returns<br/>- Strategy effectiveness<br/>- Comparative analysis<br/>- Optimization suggestions]
    
    FundSubaccount --> SubaccountActive[✅ Subaccount Active<br/>Ready for strategy execution]
    TransferCollateral --> TransferComplete[✅ Transfer Complete<br/>Funds reallocated successfully]
    TransferPositions --> TransferComplete
    DelegatePermissions --> DelegateActive[✅ Delegate Access Granted<br/>Third-party trading enabled]
    RiskParameters --> RiskConfigured[✅ Risk Controls Active<br/>Safety parameters enforced]
    PerformanceMetrics --> OptimizedStrategy[🎯 Strategy Optimized<br/>Data-driven improvements]
    
    SingleFeatures --> ContinueSimple[Continue with single account<br/>Always can upgrade later]
    SubaccountActive --> AdvancedTrading[🚀 Advanced Multi-Account Trading<br/>Professional-grade features]
    TransferComplete --> AdvancedTrading
    DelegateActive --> AdvancedTrading
    RiskConfigured --> AdvancedTrading
    OptimizedStrategy --> AdvancedTrading
    ContinueSimple --> BasicTrading[📱 Single Account Trading<br/>Simple and effective]
    
    style SubaccountStart fill:#e3f2fd
    style AdvancedTrading fill:#c8e6c9
    style BasicTrading fill:#e8f5e8
    style CreateNew fill:#fff3e0
    style SetDelegates fill:#f3e5f5
    style DelegateActive fill:#ffecb3
```

## Versioned Transactions & Advanced Features

```mermaid
flowchart TD
    AdvancedFeatures([Advanced Trading Features]) --> VersionedTx[🔄 Versioned Transactions<br/>Enhanced transaction efficiency]
    
    VersionedTx --> TxBenefits[✨ Transaction Benefits<br/>- Lower fees<br/>- Faster execution<br/>- Higher success rate<br/>- Batch operations<br/>- Complex multi-step trades]
    
    TxBenefits --> TxConfiguration[⚙️ Transaction Configuration<br/>Auto-enabled for all users<br/>Transparent optimization]
    
    TxConfiguration --> AutoConfirm{Auto-Confirm Available?}
    AutoConfirm -->|Phantom| PhantomAutoConfirm[🦄 Phantom Auto-Confirm<br/>1. Phantom Settings<br/>2. Connected Apps<br/>3. Select Drift<br/>4. Toggle Auto-Confirm<br/>5. One-click trading]
    
    AutoConfirm -->|Other Wallets| ManualConfirm[✋ Manual Confirmation<br/>- Sign each transaction<br/>- Review before approval<br/>- Maximum security<br/>- Slower execution]
    
    PhantomAutoConfirm --> TradingEfficiency[⚡ Enhanced Trading Efficiency<br/>- Instant order execution<br/>- Reduced clicks<br/>- Seamless experience<br/>- Professional-grade speed]
    
    ManualConfirm --> SecurityFirst[🔒 Security-First Trading<br/>- Review every transaction<br/>- Prevent mistakes<br/>- Educational approach<br/>- Conscious decision making]
    
    TradingEfficiency --> AdvancedOrders[📋 Advanced Order Types<br/>Complex trading strategies]
    SecurityFirst --> AdvancedOrders
    
    AdvancedOrders --> OrderTypes[🎯 Available Order Types<br/>- Market orders<br/>- Limit orders<br/>- Stop loss orders<br/>- Take profit orders<br/>- Trailing stops<br/>- Conditional orders<br/>- Iceberg orders<br/>- Time-based orders]
    
    OrderTypes --> BatchOperations[📦 Batch Operations<br/>- Multiple orders at once<br/>- Portfolio rebalancing<br/>- Risk management<br/>- Strategy execution<br/>- Capital efficiency]
    
    BatchOperations --> CrossCollateral[💎 Cross-Collateral Benefits<br/>- Use any asset as collateral<br/>- Capital efficiency<br/>- Simplified margin management<br/>- Risk optimization]
    
    CrossCollateral --> SupportedAssets[🪙 Supported Collateral Assets<br/>- USDC (primary)<br/>- SOL (native)<br/>- BTC (wrapped)<br/>- ETH (wrapped)<br/>- Additional tokens<br/>- Real-time valuations]
    
    SupportedAssets --> RiskEngine[⚠️ Advanced Risk Engine<br/>- Real-time monitoring<br/>- Account health tracking<br/>- Liquidation protection<br/>- Margin optimization<br/>- Risk alerts]
    
    RiskEngine --> HealthMonitoring[📊 Account Health Monitoring<br/>- Health ratio display<br/>- Risk level indicators<br/>- Margin requirements<br/>- Liquidation warnings<br/>- Proactive alerts]
    
    HealthMonitoring --> TradingReady[🚀 Advanced Trading Ready<br/>All features optimized<br/>Professional-grade platform]
    
    style AdvancedFeatures fill:#e3f2fd
    style TradingReady fill:#c8e6c9
    style PhantomAutoConfirm fill:#dda0dd
    style TradingEfficiency fill:#e8f5e8
    style SecurityFirst fill:#fff3e0
    style RiskEngine fill:#ffebee
```

## Account Management & Exit Strategies

```mermaid
flowchart TD
    AccountMgmt([Account Management Options]) --> ManagementChoice{Choose Management Action}
    
    ManagementChoice -->|Optimize| OptimizeAccount[⚙️ Account Optimization<br/>- Review performance<br/>- Adjust strategies<br/>- Rebalance portfolio<br/>- Update risk settings]
    
    ManagementChoice -->|Withdraw| WithdrawFunds[💸 Withdraw Funds<br/>- Partial withdrawal<br/>- Keep account active<br/>- Maintain trading access<br/>- Flexible funding]
    
    ManagementChoice -->|Pause| PauseTrading[⏸️ Pause Trading<br/>- Close all positions<br/>- Keep account open<br/>- Withdraw most funds<br/>- Maintain minimal balance]
    
    ManagementChoice -->|Exit| ExitStrategy[🚪 Complete Exit Strategy<br/>- Close all positions<br/>- Withdraw all funds<br/>- Delete account<br/>- Reclaim rent]
    
    OptimizeAccount --> OptimizationOptions[🎯 Optimization Options<br/>- Performance analysis<br/>- Strategy refinement<br/>- Risk adjustment<br/>- Capital allocation<br/>- Feature utilization]
    
    WithdrawFunds --> WithdrawChecks[✅ Withdrawal Prerequisites<br/>- Sufficient free collateral<br/>- No open positions (for full)<br/>- Settled P&L<br/>- Account health check]
    
    WithdrawChecks --> WithdrawProcess[💰 Withdrawal Process<br/>1. Select withdrawal amount<br/>2. Choose destination<br/>3. Confirm transaction<br/>4. Pay network fees<br/>5. Receive confirmation]
    
    PauseTrading --> PauseSteps[⏸️ Pause Trading Steps<br/>1. Close all open positions<br/>2. Settle unsettled P&L<br/>3. Withdraw excess funds<br/>4. Keep minimum balance<br/>5. Account remains active]
    
    ExitStrategy --> ExitPrerequisites[📋 Exit Prerequisites Check<br/>- Close all positions<br/>- Settle all P&L<br/>- Clear all borrows<br/>- Withdraw all balances<br/>- Cancel limit orders]
    
    ExitPrerequisites --> ExitChecklist{Exit Requirements Met?}
    ExitChecklist -->|No| ResolveIssues[🔧 Resolve Outstanding Issues<br/>- Close remaining positions<br/>- Settle pending P&L<br/>- Repay any borrows<br/>- Clear all balances<br/>- Cancel pending orders]
    
    ExitChecklist -->|Yes| AccountDeletion[🗑️ Account Deletion Process<br/>Safe to proceed with deletion]
    
    ResolveIssues --> ExitChecklist
    
    AccountDeletion --> DeletionOptions[🚪 Deletion Options<br/>- Single subaccount deletion<br/>- Complete account deletion<br/>- Rent reclamation<br/>- Data export options]
    
    DeletionOptions --> RentReclaim[💰 Rent Reclamation<br/>- Base rent: ~0.035 SOL<br/>- Excess fees (if applicable)<br/>- 7-day waiting period for excess<br/>- Instant base rent return<br/>- Automatic to wallet]
    
    RentReclaim --> ConfirmDeletion[⚠️ Confirm Deletion<br/>- Permanent action warning<br/>- Data loss notification<br/>- Account history deletion<br/>- No recovery possible<br/>- Final confirmation required]
    
    ConfirmDeletion --> DeletionComplete[✅ Account Deleted Successfully<br/>- Rent returned to wallet<br/>- Account permanently closed<br/>- Data cleared from system<br/>- Can create new account anytime]
    
    OptimizationOptions --> ContinueTrading[📈 Continue Optimized Trading<br/>Improved strategy execution]
    WithdrawProcess --> FlexibleAccount[💎 Flexible Account Management<br/>Funds withdrawn, account active]
    PauseSteps --> PausedAccount[⏸️ Account Paused<br/>Ready to resume when needed]
    
    DeletionComplete --> FutureOptions[🔄 Future Options<br/>- Create new account anytime<br/>- Same wallet, fresh start<br/>- No restrictions<br/>- Previous history cleared<br/>- Standard setup fees apply]
    
    style AccountMgmt fill:#e3f2fd
    style ContinueTrading fill:#c8e6c9
    style FlexibleAccount fill:#e8f5e8
    style PausedAccount fill:#fff3e0
    style DeletionComplete fill:#ffcdd2
    style FutureOptions fill:#f0f4c3
    style ConfirmDeletion fill:#ffebee
    style ExitStrategy fill:#fff3e0
```

## Complete Feature Integration Map

```mermaid
flowchart LR
    UserJourney[Complete User Journey] --> Authentication[🔐 Authentication Layer]
    Authentication --> WalletMgmt[👛 Wallet Management]
    WalletMgmt --> AccountSetup[⚙️ Account Setup]
    AccountSetup --> TradingEngine[📈 Trading Engine]
    TradingEngine --> RiskMgmt[⚠️ Risk Management]
    RiskMgmt --> Portfolio[📊 Portfolio Management]
    Portfolio --> Exit[🚪 Exit Strategies]
    
    Authentication --> SocialLogin[📧 Social Login<br/>- Email/Google/Apple<br/>- Magic Wallet<br/>- Recovery options]
    Authentication --> CryptoWallets[🦄 Crypto Wallets<br/>- Phantom<br/>- MetaMask<br/>- Hardware wallets]
    
    WalletMgmt --> MultiWallet[🔗 Multi-Wallet Support<br/>- 20+ wallet options<br/>- Hardware integration<br/>- Security features]
    WalletMgmt --> FundingMethods[💰 Funding Methods<br/>- Fiat on-ramps<br/>- CEX transfers<br/>- Cross-chain bridges]
    
    AccountSetup --> Subaccounts[📁 Subaccounts<br/>- Multiple strategies<br/>- Risk isolation<br/>- Performance tracking]
    AccountSetup --> Delegation[👥 Delegation<br/>- Third-party access<br/>- Permission management<br/>- Institutional features]
    
    TradingEngine --> VersionedTx[🔄 Versioned Transactions<br/>- Lower fees<br/>- Faster execution<br/>- Batch operations]
    TradingEngine --> AutoConfirm[⚡ Auto-Confirm<br/>- One-click trading<br/>- Enhanced UX<br/>- Professional speed]
    
    RiskMgmt --> CrossCollateral[💎 Cross-Collateral<br/>- Multi-asset support<br/>- Capital efficiency<br/>- Real-time valuation]
    RiskMgmt --> HealthMonitoring[📊 Health Monitoring<br/>- Real-time tracking<br/>- Risk alerts<br/>- Liquidation protection]
    
    Portfolio --> AdvancedOrders[🎯 Advanced Orders<br/>- Complex strategies<br/>- Risk management<br/>- Automation features]
    Portfolio --> PerformanceTracking[📈 Performance Tracking<br/>- Strategy analysis<br/>- P&L attribution<br/>- Optimization insights]
    
    Exit --> PartialWithdraw[💸 Partial Withdrawal<br/>- Flexible funding<br/>- Active account<br/>- Continued access]
    Exit --> CompleteExit[🗑️ Complete Exit<br/>- Account deletion<br/>- Rent reclamation<br/>- Fresh start option]
    
    style UserJourney fill:#e3f2fd
    style Authentication fill:#e8f5e8
    style TradingEngine fill:#fff3e0
    style RiskMgmt fill:#ffebee
    style Exit fill:#f3e5f5
```

---

## Implementation Guide

### Key Features Covered:
1. **Complete Wallet Support** - Social login, Phantom, MetaMask, hardware wallets
2. **MetaMask Integration** - Detailed Solana network setup and configuration
3. **Passwordless Authentication** - Magic wallet, social providers, email verification
4. **Advanced Subaccounts** - Multiple strategies, risk isolation, delegation
5. **Versioned Transactions** - Optimized performance, lower fees, batch operations
6. **Auto-Confirm Features** - One-click trading, enhanced UX
7. **Risk Management** - Cross-collateral, health monitoring, liquidation protection
8. **Account Management** - Withdrawal options, account closure, rent reclamation

### Technical Implementation Notes:
- **MetaMask Solana Setup**: Manual network configuration required
- **Social Login**: Magic wallet integration with email recovery
- **Subaccounts**: Numbered accounts (0, 1, 2...) with individual settings
- **Delegated Accounts**: Authority mapping for institutional use
- **Versioned Transactions**: Automatically enabled, transparent to users
- **Account Deletion**: Permanent action with rent reclamation

### Security Considerations:
- **Progressive Security**: Start simple, upgrade as needed
- **Multi-Factor Authentication**: Available with social login
- **Hardware Wallet Integration**: Maximum security for large amounts
- **Risk Parameter Controls**: Individual and account-level limits
- **Audit Trails**: Complete transaction and delegation history

These comprehensive flowcharts now include all advanced Drift Protocol features, providing complete coverage of the user journey from basic signup to professional-grade trading with institutional features.