# Drift Protocol User Journey Flows - Complete Wallet Options

Based on official documentation from https://docs.drift.trade/ and https://app.drift.trade

## Journey 1: Perpetual Trading Flow (Complete Wallet Options)

```mermaid
flowchart TD
    Start([New User Wants to Trade Perps]) --> WalletCheck{Has Crypto Wallet?}
    
    WalletCheck -->|No| WalletChoice{Preferred Setup Method?}
    WalletCheck -->|Yes| WalletType{What Wallet Type?}
    
    WalletChoice -->|Easy & Fast| SocialLogin[🔐 Social Login<br/>- Email signup<br/>- Passwordless login<br/>- No seed phrase needed]
    WalletChoice -->|Full Control| CreateWallet[Create Crypto Wallet<br/>Choose wallet type]
    
    SocialLogin --> SocialSetup[Complete Social Setup<br/>- Verify email<br/>- Set up security<br/>- Auto-generate wallet]
    CreateWallet --> WalletOptions{Select Wallet}
    
    WalletOptions -->|Recommended| PhantomSetup[🦄 Phantom Wallet<br/>- Native Solana support<br/>- Browser extension<br/>- Mobile app available]
    WalletOptions -->|Popular| MetaMaskSetup[🦊 MetaMask<br/>- Multi-chain support<br/>- Add Solana network<br/>- Browser extension]
    WalletOptions -->|Advanced| OtherWallets[Other Wallets<br/>- Solflare<br/>- Glow<br/>- Ledger hardware]
    
    PhantomSetup --> PhantomSteps[Phantom Setup<br/>- Install extension<br/>- Create new wallet<br/>- Secure seed phrase]
    MetaMaskSetup --> MetaMaskSteps[MetaMask Setup<br/>- Install extension<br/>- Add Solana network<br/>- Import/create wallet]
    OtherWallets --> OtherSteps[Alternative Setup<br/>- Follow wallet instructions<br/>- Ensure Solana support]
    
    WalletType -->|Phantom| PhantomSteps
    WalletType -->|MetaMask| MetaMaskSteps
    WalletType -->|Other| OtherSteps
    WalletType -->|Social| SocialSetup
    
    SocialSetup --> CheckSOL{Has SOL for fees?}
    PhantomSteps --> CheckSOL
    MetaMaskSteps --> CheckSOL
    OtherSteps --> CheckSOL
    
    CheckSOL -->|No| GetSOLMethod{How to Get SOL?}
    CheckSOL -->|Yes| ConnectDrift[Connect to app.drift.trade]
    
    GetSOLMethod -->|Buy Direct| BuySOLDirect[Buy SOL Directly<br/>- In-wallet purchase<br/>- Credit card/bank<br/>- Built-in exchanges]
    GetSOLMethod -->|CEX Transfer| BuySOLCEX[CEX Method<br/>- Buy on Binance/Coinbase<br/>- Withdraw to wallet<br/>- Check network = Solana]
    GetSOLMethod -->|Bridge| BridgeAssets[Bridge from Other Chains<br/>- Use recommended bridges<br/>- Convert ETH/USDC to Solana<br/>- Cross-chain transfer]
    
    BuySOLDirect --> ConnectDrift
    BuySOLCEX --> ConnectDrift
    BridgeAssets --> ConnectDrift
    
    ConnectDrift --> WalletConnect[Connect Wallet to Drift<br/>- Click 'Connect Wallet'<br/>- Select your wallet type<br/>- Approve connection]
    
    WalletConnect --> AuthMethod{Authentication Method}
    AuthMethod -->|Wallet| SignMessage[Sign Connection Message<br/>- Verify wallet ownership<br/>- No fees for connection]
    AuthMethod -->|Social| SocialAuth[Social Authentication<br/>- Verify email/social<br/>- Automatic wallet linking]
    
    SignMessage --> AccountSetup[Account Setup<br/>- Pay 0.035 SOL setup fee<br/>- Initialize Drift account<br/>- Create subaccount]
    SocialAuth --> AccountSetup
    
    AccountSetup --> Deposit[Deposit Collateral<br/>- USDC recommended<br/>- SOL, BTC, ETH accepted<br/>- Min $100-500 suggested]
    
    Deposit --> DepositMethod{Deposit Method}
    DepositMethod -->|Direct| DirectDeposit[Direct Wallet Deposit<br/>- From connected wallet<br/>- Instant transfer<br/>- Gas fees apply]
    DepositMethod -->|CEX| CEXDeposit[CEX Withdrawal<br/>- Withdraw from exchange<br/>- To Drift wallet address<br/>- Check network compatibility]
    DepositMethod -->|Cross-chain| CrossChainDeposit[Cross-chain Bridge<br/>- Bridge tokens to Solana<br/>- Then deposit to Drift<br/>- Multi-step process]
    
    DirectDeposit --> CheckBalance[Verify Account Balance<br/>& Free Collateral]
    CEXDeposit --> CheckBalance
    CrossChainDeposit --> CheckBalance
    
    CheckBalance --> SelectMarket[Choose Perp Market<br/>- SOL-PERP popular<br/>- Analyze volume & funding<br/>- Check mark vs oracle price]
    
    SelectMarket --> PlanTrade[Plan Trade<br/>- Direction: Long/Short<br/>- Position size calculation<br/>- Leverage 1x-101x selection]
    
    PlanTrade --> OrderType{Select Order Type}
    OrderType -->|Market| PlaceMarket[Market Order<br/>- Immediate execution<br/>- Current market price<br/>- Set size & leverage]
    OrderType -->|Limit| PlaceLimit[Limit Order<br/>- Set target price<br/>- Set size & leverage<br/>- Wait for price trigger]
    OrderType -->|Advanced| PlaceAdvanced[Advanced Orders<br/>- Stop Loss/Take Profit<br/>- Trailing stops<br/>- Conditional orders]
    
    PlaceMarket --> ReviewOrder[Review Trade Summary<br/>- Entry price estimate<br/>- Trading fees ~0.1%<br/>- Margin requirement<br/>- Liquidation price]
    PlaceLimit --> ReviewOrder
    PlaceAdvanced --> ReviewOrder
    
    ReviewOrder --> ConfirmTrade[Confirm Transaction<br/>- Final review<br/>- Sign with wallet<br/>- Submit to network]
    
    ConfirmTrade --> JITAuction[🔄 5-Second JIT Auction<br/>Dutch auction mechanism<br/>Market makers compete<br/>Price improvement opportunity]
    
    JITAuction --> ExecutionPath{Execution Route}
    ExecutionPath -->|JIT Fill| JITFill[✅ JIT Market Maker Fill<br/>- Better than expected price<br/>- Instant execution<br/>- Optimal liquidity]
    ExecutionPath -->|DLOB Match| DLOBFill[✅ DLOB Limit Order Match<br/>- Matched with existing order<br/>- Fair price execution<br/>- Decentralized matching]
    ExecutionPath -->|AMM Fill| AMMFill[✅ AMM Backstop Fill<br/>- Guaranteed execution<br/>- AMM liquidity source<br/>- Constant availability]
    
    JITFill --> MonitorPosition[🎯 Position Active<br/>Monitor in Positions tab<br/>Real-time updates<br/>Mobile notifications available]
    DLOBFill --> MonitorPosition
    AMMFill --> MonitorPosition
    
    MonitorPosition --> TrackMetrics[📊 Track Real-time Metrics<br/>- Unrealized P&L<br/>- Mark price changes<br/>- Funding payments hourly<br/>- Account health status]
    
    TrackMetrics --> ManagePosition{Position Management?}
    ManagePosition -->|Adjust| AdjustOptions[⚙️ Adjustment Options<br/>- Increase position size<br/>- Reduce position size<br/>- Set stop-loss orders<br/>- Take profit targets]
    ManagePosition -->|Hold| ContinueMonitor[👀 Continue Monitoring<br/>- Watch market conditions<br/>- Monitor health ratio<br/>- Track funding rates]
    ManagePosition -->|Close| ClosePosition[🚪 Close Position<br/>- Full position close<br/>- Partial position close<br/>- Market or limit close]
    
    AdjustOptions --> TrackMetrics
    ContinueMonitor --> TrackMetrics
    ClosePosition --> SettlePNL[💰 Settle P&L<br/>- Calculate final P&L<br/>- Update account balance<br/>- Pay closing fees]
    
    SettlePNL --> WithdrawOption{Withdraw Funds?}
    WithdrawOption -->|Yes| WithdrawFunds[💸 Withdraw to Wallet<br/>- Back to connected wallet<br/>- Or to external address<br/>- Choose withdrawal amount]
    WithdrawOption -->|No| KeepFunds[💎 Keep in Drift<br/>- Available for next trade<br/>- Earn lending yield<br/>- Use as collateral]
    
    WithdrawFunds --> AnalyzePerformance[📈 Analyze Performance<br/>- Total return calculation<br/>- Fees breakdown<br/>- Time in position<br/>- Learning insights]
    KeepFunds --> AnalyzePerformance
    
    AnalyzePerformance --> Complete([✅ Trading Journey Complete<br/>Ready for next trade])
    
    style Start fill:#e3f2fd
    style Complete fill:#c8e6c9
    style SocialLogin fill:#e8f5e8
    style JITAuction fill:#fff3e0
    style ExecutionPath fill:#f3e5f5
    style MonitorPosition fill:#e1f5fe
```

## Wallet Setup Decision Flow

```mermaid
flowchart TD
    WalletDecision([Choose Wallet Setup Method]) --> UserType{User Preference?}
    
    UserType -->|Simple & Fast| SocialPath[🔐 Social Login Path<br/>Recommended for beginners]
    UserType -->|Full Control| WalletPath[👛 Crypto Wallet Path<br/>Recommended for experienced]
    UserType -->|Maximum Security| HardwarePath[🔒 Hardware Wallet Path<br/>Recommended for large amounts]
    
    SocialPath --> SocialOptions{Social Login Options}
    SocialOptions -->|Email| EmailLogin[📧 Email Signup<br/>- Enter email address<br/>- Verify email code<br/>- Set password<br/>- Auto-wallet creation]
    SocialOptions -->|Google| GoogleLogin[🔍 Google Account<br/>- OAuth with Google<br/>- Instant verification<br/>- Linked wallet creation]
    SocialOptions -->|Apple| AppleLogin[🍎 Apple ID<br/>- Sign in with Apple<br/>- Privacy-focused<br/>- Seamless integration]
    SocialOptions -->|Discord| DiscordLogin[💬 Discord Account<br/>- Connect Discord<br/>- Community integration<br/>- Social verification]
    
    WalletPath --> WalletChoice{Select Wallet Type}
    WalletChoice -->|Recommended| Phantom[🦄 Phantom Wallet<br/>✅ Native Solana support<br/>✅ User-friendly interface<br/>✅ Mobile + Desktop<br/>✅ Built-in swap features]
    WalletChoice -->|Popular| MetaMask[🦊 MetaMask<br/>✅ Multi-chain support<br/>✅ Large ecosystem<br/>⚠️ Requires Solana setup<br/>✅ Familiar interface]
    WalletChoice -->|Alternative| OtherOptions[🔧 Other Wallets<br/>- Solflare: Solana-native<br/>- Glow: Solana-focused<br/>- Backpack: Multi-chain<br/>- Coinbase Wallet: CEX integration]
    
    HardwarePath --> HardwareChoice{Hardware Wallet}
    HardwareChoice -->|Popular| Ledger[📟 Ledger<br/>- Nano S/X/S Plus<br/>- Install Solana app<br/>- Use with Phantom/Solflare<br/>- Maximum security]
    HardwareChoice -->|Alternative| Trezor[🔐 Trezor<br/>- Model T/One<br/>- Limited Solana support<br/>- Check compatibility<br/>- Third-party integration]
    
    EmailLogin --> SocialSetup[Complete Social Setup<br/>- Account verification<br/>- Security settings<br/>- Backup options<br/>- Recovery methods]
    
    GoogleLogin --> SocialSetup
    AppleLogin --> SocialSetup
    DiscordLogin --> SocialSetup
    
    Phantom --> PhantomGuide[📱 Phantom Setup Guide<br/>1. Visit phantom.app<br/>2. Download for browser/mobile<br/>3. Create new wallet<br/>4. Secure 12-word phrase<br/>5. Set strong password]
    
    MetaMask --> MetaMaskGuide[🦊 MetaMask Setup Guide<br/>1. Install MetaMask extension<br/>2. Create/import wallet<br/>3. Add Solana network manually<br/>4. Configure RPC settings<br/>5. Test connection]
    
    OtherOptions --> OtherGuide[🔧 Alternative Setup<br/>1. Choose preferred wallet<br/>2. Follow wallet instructions<br/>3. Ensure Solana compatibility<br/>4. Test functionality<br/>5. Backup recovery info]
    
    Ledger --> HardwareGuide[📟 Hardware Setup<br/>1. Set up Ledger device<br/>2. Install Solana app<br/>3. Connect to Phantom/Solflare<br/>4. Verify connection<br/>5. Test small transaction]
    Trezor --> HardwareGuide
    
    SocialSetup --> Features[🎯 Social Login Features<br/>✅ No seed phrase needed<br/>✅ Email recovery<br/>✅ Familiar login process<br/>⚠️ Less decentralized<br/>✅ Perfect for beginners]
    
    PhantomGuide --> PhantomFeatures[🦄 Phantom Features<br/>✅ Built-in Solana DEX<br/>✅ NFT support<br/>✅ Staking integration<br/>✅ Mobile DApp browser<br/>✅ Auto-confirm option]
    
    MetaMaskGuide --> MetaMaskFeatures[🦊 MetaMask Features<br/>✅ Multi-chain portfolio<br/>✅ Large DApp ecosystem<br/>✅ Hardware wallet support<br/>⚠️ Solana setup required<br/>✅ Advanced features]
    
    OtherGuide --> AlternativeFeatures[🔧 Alternative Features<br/>- Solflare: Advanced Solana tools<br/>- Glow: Simplicity focused<br/>- Backpack: xNFT support<br/>- Research specific benefits]
    
    HardwareGuide --> SecurityFeatures[🔒 Hardware Security<br/>✅ Private keys offline<br/>✅ Transaction signing secure<br/>✅ Immune to malware<br/>⚠️ Physical device needed<br/>✅ Highest security level]
    
    Features --> Ready[✅ Wallet Ready for Drift]
    PhantomFeatures --> Ready
    MetaMaskFeatures --> Ready
    AlternativeFeatures --> Ready
    SecurityFeatures --> Ready
    
    Ready --> ConnectToDrift[🚀 Connect to Drift Protocol<br/>Navigate to app.drift.trade]
    
    style WalletDecision fill:#e3f2fd
    style Ready fill:#c8e6c9
    style SocialPath fill:#e8f5e8
    style WalletPath fill:#f3e5f5
    style HardwarePath fill:#ffecb3
    style Features fill:#e0f2f1
```

## Onboarding Flow with All Login Options

```mermaid
flowchart TD
    Landing([User Visits app.drift.trade]) --> LoginPrompt[Connect Wallet Button<br/>Multiple options available]
    
    LoginPrompt --> LoginChoice{Choose Login Method}
    
    LoginChoice -->|Fastest| Social[🔐 Social Login<br/>No wallet needed<br/>1-click signup]
    LoginChoice -->|Popular| Phantom[🦄 Phantom<br/>Recommended Solana wallet<br/>Best experience]
    LoginChoice -->|Multi-chain| MetaMask[🦊 MetaMask<br/>Connect existing wallet<br/>Multi-chain support]
    LoginChoice -->|Other| MoreWallets[⚙️ More Wallets<br/>20+ wallet options<br/>Choose your preference]
    
    Social --> SocialFlow[Social Authentication<br/>- Choose provider<br/>- Verify account<br/>- Auto-generate wallet<br/>- Skip seed phrase]
    
    Phantom --> PhantomFlow{Phantom Status?}
    PhantomFlow -->|Installed| PhantomConnect[Connect Phantom<br/>- Approve connection<br/>- Sign message<br/>- Access granted]
    PhantomFlow -->|Not Installed| PhantomInstall[Install Phantom<br/>- Redirect to phantom.app<br/>- Download extension<br/>- Setup new wallet<br/>- Return to Drift]
    
    MetaMask --> MetaMaskFlow{MetaMask Status?}
    MetaMaskFlow -->|Installed| MetaMaskCheck{Solana Network?}
    MetaMaskFlow -->|Not Installed| MetaMaskInstall[Install MetaMask<br/>- Redirect to metamask.io<br/>- Download extension<br/>- Setup wallet<br/>- Return to Drift]
    
    MetaMaskCheck -->|Configured| MetaMaskConnect[Connect MetaMask<br/>- Switch to Solana<br/>- Approve connection<br/>- Sign message]
    MetaMaskCheck -->|Need Setup| MetaMaskSetup[Setup Solana Network<br/>- Add network manually<br/>- Configure RPC<br/>- Test connection]
    
    MoreWallets --> WalletGrid[Wallet Selection Grid<br/>- Solflare<br/>- Glow<br/>- Backpack<br/>- Coinbase Wallet<br/>- Exodus<br/>- Trust Wallet<br/>- Slope<br/>- And 15+ more options]
    
    SocialFlow --> Authenticated[✅ Authenticated<br/>Social wallet created<br/>Ready to deposit]
    PhantomConnect --> Authenticated
    PhantomInstall --> PhantomConnect
    MetaMaskConnect --> Authenticated
    MetaMaskInstall --> MetaMaskSetup
    MetaMaskSetup --> MetaMaskConnect
    WalletGrid --> WalletConnect[Connect Selected Wallet<br/>Follow wallet-specific flow]
    WalletConnect --> Authenticated
    
    Authenticated --> OnboardingCheck{First Time User?}
    OnboardingCheck -->|Yes| Onboarding[🎓 Onboarding Experience<br/>- Welcome tutorial<br/>- Feature walkthrough<br/>- Risk warnings<br/>- Best practices<br/>- Demo trade option]
    OnboardingCheck -->|No| ExistingUser[👋 Welcome Back<br/>- Load user data<br/>- Check account health<br/>- Show portfolio<br/>- Recent activity]
    
    Onboarding --> AccountSetup[Account Initialization<br/>- Pay 0.035 SOL fee<br/>- Create subaccount<br/>- Set preferences<br/>- Choose default settings]
    ExistingUser --> Dashboard[📊 Dashboard Access<br/>Account overview loaded]
    
    AccountSetup --> FirstDeposit[💰 First Deposit Guide<br/>- Funding options<br/>- Minimum amounts<br/>- Supported assets<br/>- Step-by-step help]
    
    FirstDeposit --> DepositMethods{Funding Method?}
    DepositMethods -->|Wallet| WalletDeposit[Direct from Wallet<br/>- Select asset<br/>- Enter amount<br/>- Confirm transaction]
    DepositMethods -->|CEX| CEXGuide[CEX Withdrawal Guide<br/>- Popular exchanges<br/>- Withdrawal instructions<br/>- Network verification<br/>- Address verification]
    DepositMethods -->|Card| FiatOnRamp[💳 Buy Crypto Direct<br/>- Credit/debit card<br/>- Bank transfer<br/>- Integrated providers<br/>- Direct to Drift]
    DepositMethods -->|Bridge| BridgeGuide[🌉 Cross-chain Bridge<br/>- Supported networks<br/>- Bridge providers<br/>- Fee estimates<br/>- Step-by-step process]
    
    WalletDeposit --> FundsReady[✅ Funds Available<br/>Ready to trade]
    CEXGuide --> FundsReady
    FiatOnRamp --> FundsReady
    BridgeGuide --> FundsReady
    Dashboard --> FundsReady
    
    FundsReady --> TradingReady[🚀 Ready to Trade<br/>Choose your journey:<br/>- Perpetual trading<br/>- Liquidity provision<br/>- Lending/borrowing<br/>- Insurance staking]
    
    style Landing fill:#e3f2fd
    style TradingReady fill:#c8e6c9
    style Social fill:#e8f5e8
    style Phantom fill:#dda0dd
    style MetaMask fill:#ffa500
    style Onboarding fill:#fff3e0
    style FiatOnRamp fill:#e1f5fe
```

## Social Login Detailed Flow

```mermaid
flowchart TD
    SocialStart([Choose Social Login]) --> Provider{Select Provider}
    
    Provider -->|Email| EmailFlow[📧 Email Registration<br/>Most universal option]
    Provider -->|Google| GoogleFlow[🔍 Google OAuth<br/>Fast & familiar]
    Provider -->|Apple| AppleFlow[🍎 Apple ID<br/>Privacy-focused]
    Provider -->|Discord| DiscordFlow[💬 Discord<br/>Crypto-native community]
    Provider -->|Twitter| TwitterFlow[🐦 Twitter/X<br/>Social verification]
    Provider -->|GitHub| GitHubFlow[⚡ GitHub<br/>Developer-friendly]
    
    EmailFlow --> EmailSteps[Email Process<br/>1. Enter email address<br/>2. Receive verification code<br/>3. Enter code + set password<br/>4. Account created<br/>5. Wallet auto-generated]
    
    GoogleFlow --> GoogleSteps[Google Process<br/>1. Click 'Continue with Google'<br/>2. Google OAuth popup<br/>3. Select Google account<br/>4. Grant permissions<br/>5. Return to Drift authenticated]
    
    AppleFlow --> AppleSteps[Apple Process<br/>1. Click 'Sign in with Apple'<br/>2. Apple ID authentication<br/>3. Face ID/Touch ID/Password<br/>4. Privacy options<br/>5. Account linking]
    
    DiscordFlow --> DiscordSteps[Discord Process<br/>1. Authorize Discord app<br/>2. Select Discord server<br/>3. Verify account standing<br/>4. Link crypto identity<br/>5. Community benefits]
    
    TwitterFlow --> TwitterSteps[Twitter Process<br/>1. Connect Twitter account<br/>2. Verify account activity<br/>3. Check follower metrics<br/>4. Social proof validation<br/>5. Enhanced features]
    
    GitHubFlow --> GitHubSteps[GitHub Process<br/>1. Authorize GitHub app<br/>2. Verify developer status<br/>3. Check repository activity<br/>4. Tech community access<br/>5. Developer features]
    
    EmailSteps --> SocialWallet[🔐 Social Wallet Created<br/>- Non-custodial<br/>- Email recovery<br/>- No seed phrase<br/>- Multi-factor auth<br/>- Biometric support]
    GoogleSteps --> SocialWallet
    AppleSteps --> SocialWallet
    DiscordSteps --> SocialWallet
    TwitterSteps --> SocialWallet
    GitHubSteps --> SocialWallet
    
    SocialWallet --> SecuritySetup[🛡️ Security Configuration<br/>- Set up 2FA<br/>- Biometric authentication<br/>- Recovery methods<br/>- Device management<br/>- Session control]
    
    SecuritySetup --> SocialFeatures[✨ Social Features<br/>✅ Passwordless login<br/>✅ Email recovery<br/>✅ No seed phrase management<br/>✅ Social verification<br/>✅ Community features<br/>⚠️ Account dependence]
    
    SocialFeatures --> FundingOptions[💰 Funding Your Social Wallet<br/>Multiple easy options]
    
    FundingOptions --> FundingChoice{Choose Funding Method}
    FundingChoice -->|Credit Card| CardPurchase[💳 Direct Card Purchase<br/>- Buy USDC/SOL directly<br/>- Integrated payment<br/>- Instant availability<br/>- Higher fees but convenient]
    FundingChoice -->|Bank Transfer| BankTransfer[🏦 Bank Transfer<br/>- ACH/wire transfer<br/>- Lower fees<br/>- 1-3 day processing<br/>- Larger amounts]
    FundingChoice -->|Crypto Transfer| CryptoTransfer[₿ Crypto Deposit<br/>- From other wallets<br/>- From exchanges<br/>- Cross-chain bridges<br/>- Standard network fees]
    FundingChoice -->|Apple Pay| ApplePay[📱 Apple Pay<br/>- iOS users<br/>- Touch/Face ID<br/>- Instant payment<br/>- Integrated experience]
    FundingChoice -->|Google Pay| GooglePay[💰 Google Pay<br/>- Android users<br/>- Biometric auth<br/>- Quick payment<br/>- Seamless flow]
    
    CardPurchase --> FundsAvailable[✅ Funds Available<br/>Ready to trade on Drift]
    BankTransfer --> FundsAvailable
    CryptoTransfer --> FundsAvailable
    ApplePay --> FundsAvailable
    GooglePay --> FundsAvailable
    
    FundsAvailable --> SocialSuccess[🎉 Social Login Success<br/>- No complex setup<br/>- Familiar login process<br/>- Easy fund management<br/>- Ready for DeFi<br/>- Beginner-friendly]
    
    style SocialStart fill:#e3f2fd
    style SocialSuccess fill:#c8e6c9
    style EmailFlow fill:#e8f5e8
    style GoogleFlow fill:#ffeaa7
    style AppleFlow fill:#dda0dd
    style DiscordFlow fill:#b19cd9
    style SocialWallet fill:#e1f5fe
    style CardPurchase fill:#81c784
```

---

## Implementation Notes

### New Wallet Support Features:
1. **Social Login Integration** - Passwordless authentication with major providers
2. **MetaMask Support** - Multi-chain wallet with Solana network setup
3. **Hardware Wallet Support** - Ledger and Trezor integration
4. **20+ Wallet Options** - Comprehensive wallet ecosystem support
5. **Fiat On-Ramps** - Direct credit card and bank transfer options

### Enhanced User Experience:
- **Smart Routing** - Users directed to best option based on preferences
- **Progressive Setup** - Start simple, add complexity as needed
- **Recovery Options** - Multiple backup and recovery methods
- **Cross-Platform** - Mobile and desktop support for all options

### Security Considerations:
- **Risk Education** - Clear warnings about different security models
- **Best Practices** - Guidance for each wallet type
- **Backup Emphasis** - Importance of proper backup procedures
- **Progressive Security** - Start simple, enhance over time

These updated flowcharts now comprehensively cover all authentication and wallet options that Drift Protocol supports, making the platform accessible to users across the entire spectrum from crypto beginners to advanced DeFi users.