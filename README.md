# 📊 IBKR Trading Dashboard

This repository demonstrates the [IBKR Auto-Exporter](https://github.com/jefrnc/ibkr-auto-exporter) GitHub Action in action!

## 🎯 What This Shows

This is a live example of:
- ✅ Automated daily trading data exports from Interactive Brokers
- ✅ Weekly performance summaries
- ✅ Monthly analytics reports
- ✅ Live statistics in README
- ✅ Interactive trading calendar
- ✅ Cost basis filtering for algorithmic trades

<!-- STATS_START -->
### 📊 Live Trading Statistics

| Period | Trades | P&L | Win Rate |
|--------|--------|-----|----------|
| **Week 30 (current)** | 116 | **-$136.39** | 29.3% |
| Week 29 | 0 | $0.00 | 0.0% |
| **July (current)** | 315 | **-$227.37** | 35.6% |
| June | 52 | **-$11.94** | 17.9% |

#### 📈 Yearly Projection

| Metric | Actual YTD | Projected EOY |
|--------|------------|---------------|
| **Trades** | 390 | 682 |
| **P&L** | **-$203.00** | **-$355.25** |

*Based on current performance with 156 days remaining*

*Last updated: 2025-07-27 19:34 UTC*
<!-- STATS_END -->

<!-- CALENDAR_START -->
## 📅 2025 Trading Calendar

![Trading Calendar](.github/assets/calendar-2025.svg)

### Legend
🟩 Profit Day | 🟨 Break Even | 🟥 Loss Day | ⬜ No Trades

### 📊 2025 Statistics

| Metric | Value |
|--------|-------|
| **Total Trading Days** | 37 |
| **Total Trades** | 390 |
| **Total P&L** | $-203.00 |
| **Win Rate** | 32.4% |
| **Profit Days** | 12 (32.4%) |
| **Loss Days** | 20 (54.1%) |
| **Best Day** | $16.52 (2025-02-05) |
| **Worst Day** | $-50.69 (2025-07-24) |
| **Daily Average** | $-5.49 |

### 📈 Monthly Breakdown

| Month | Trades | P&L | Win Rate |
|-------|--------|-----|----------|
| January | 4 | **+$11.26** | 66.7% |
| February | 10 | **+$16.08** | 33.3% |
| March | 1 | **-$0.52** | 0.0% |
| April | 2 | **-$3.19** | 0.0% |
| May | 6 | **+$12.68** | 100.0% |
| June | 52 | **-$11.94** | 60.0% |
| July | 315 | **-$227.37** | 11.8% |

<!-- CALENDAR_END -->

## 🚀 Features Demonstrated

### 1. Automated Exports
Every day at 10 PM EST, this workflow automatically:
- Downloads trading data from IBKR via Flex Web Service
- Processes and organizes trades by date
- Calculates P&L and performance metrics
- Commits to Git for version control

### 2. Data Structure
```
exports/
├── daily/          # Daily trade data
│   └── 2025-07-27.json
├── weekly/         # Weekly summaries
│   └── 2025-W30.json
└── monthly/        # Monthly reports
    └── 2025-07.json
```

### 3. Cost Basis Filtering
This example filters only algorithmic trades with cost basis between $0-$50, perfect for:
- Small position algorithmic trading
- Scalping strategies
- Testing new algorithms with limited risk

## 🔧 Setup Your Own

1. **Fork this repository** or create a new one
2. **Add secrets** to your repository:
   - `IBKR_TOKEN`: Your Flex Web Service token
   - `IBKR_QUERY_ID`: Your Flex Query ID
3. **Configure filtering** (optional) in the workflow
4. **That's it!** Data will start flowing automatically

## 📈 View the Dashboard

*Dashboard coming soon*

## 🔒 Security

- Token-based authentication (no passwords)
- Account numbers automatically obfuscated
- Data stays in your private repository

## 📝 Workflow Configuration

```yaml
name: Export IBKR Trading Data

on:
  schedule:
    - cron: '0 3 * * *'  # Daily at 10 PM EST
  workflow_dispatch:     # Manual trigger

jobs:
  export:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    
    steps:
    - uses: actions/checkout@v3
    
    - uses: jefrnc/ibkr-auto-exporter@v1
      with:
        ibkr-token: ${{ secrets.IBKR_TOKEN }}
        ibkr-query-id: ${{ secrets.IBKR_QUERY_ID }}
        cost-basis-min: '0'
        cost-basis-max: '50'
```

## 🎨 Customization Options

The action supports many parameters:
- `export-path`: Custom directory for exports
- `obfuscate-account`: Privacy mode
- `generate-weekly`: Force weekly summaries
- `generate-monthly`: Force monthly reports
- `cost-basis-min/max`: Filter trades by size

## 📊 Example Data

<details>
<summary>Daily Export Sample</summary>

```json
{
  "exportDate": "2025-07-27 16:00:00",
  "account": "U*****98",
  "date": "2025-07-27",
  "trades": [
    {
      "symbol": "AAPL",
      "side": "BUY",
      "quantity": 1,
      "price": 45.25,
      "pnl": 2.50
    }
  ],
  "summary": {
    "totalTrades": 15,
    "totalPnL": 125.75,
    "winRate": 0.73
  }
}
```
</details>

## 🤝 Contributing

Found a bug or have a suggestion? Please open an issue in the [main repository](https://github.com/jefrnc/ibkr-auto-exporter).

## 📄 License

This example is MIT licensed. The IBKR Auto-Exporter action is also MIT licensed.

---

⭐ If this helps you, please star the [main repository](https://github.com/jefrnc/ibkr-auto-exporter)!

Built with ❤️ using [IBKR Auto-Exporter](https://github.com/jefrnc/ibkr-auto-exporter)