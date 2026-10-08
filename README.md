# Personal Finance Dashboard

A single-file, offline-first personal finance dashboard built for Ghanaian users. No server, no database, no tracking — just open the HTML file in your browser.

## Features

- **Overview** — Income, spend, net savings, and savings streak at a glance
- **Financial Health Score** — 0-100 score based on savings rate, budget adherence, subscription control, and tracking consistency
- **Categories** — Donut chart and ranking of spending by category
- **Transfers** — Track tithe, taxes, and savings allocations per month
- **Transactions** — Search, filter, and mark subscriptions as "could cancel" or "canceled"
- **Month vs Month** — Income vs spend bars and category trends
- **Budget** — Set monthly targets per category with visual progress bars
- **Insights** — Auto-generated analysis of your spending patterns
- **Super Savings** — Identifies cuttable non-essential spending
- **Charts** — Daily spending line chart, income allocation pie, stacked category bars, and a 30-day heatmap
- **Stocks** — Ghana Stock Exchange (GSE) market overview with gainers, losers, and dividend stocks
- **Allocation** — Cash-flow allocation based on the 55/12.5/10 rule (survival/wealth/discretionary)
- **Dark/Light theme** — Toggle between dark and light mode
- **Daily Money Tips** — Rotating financial tips on the overview page
- **Sample data included** — Works out of the box with realistic Ghanaian sample data

## How to Use

### Quick Start

1. **Download** the `dashboard.html` file from this repo
2. **Open** it in any modern browser (Chrome, Firefox, Edge, Brave)
3. That's it — the dashboard loads with sample data

### Customize with Your Own Data

1. Open `dashboard.html` in a text editor (Notepad, VS Code, anything)
2. Find the `DATA` object near the top of the `<script>` section
3. Replace the sample transactions with your own:

```javascript
const DATA = {
  "generated": "2026-10-08 10:00",
  "title": "My Finance Dashboard",
  "currency": "GHS ",  // Change to your currency symbol
  "bookkeeping_type": "personal",
  "percentages": { "taxes": 0, "tithe": 10, "savings": 20 },
  "budgets": {
    "Groceries": 800,
    "Transportation": 300,
    "Utilities": 250,
    "Dining": 200,
    "Entertainment": 100
  },
  "months": ["2026-08", "2026-09", "2026-10"],
  "transactions": [
    // Your transactions here
    { "date": "2026-10-01", "month": "2026-10", "description": "Salary", "amount": 3500.0, "category": "Income", "status": "", "source": "my-data.csv", "id": "unique-id-1" },
    { "date": "2026-10-03", "month": "2026-10", "description": "Shoprite", "amount": -180.50, "category": "Groceries", "status": "", "source": "my-data.csv", "id": "unique-id-2" }
  ],
  "recurring": [],
  "uncategorized": [],
  "sources": ["my-data.csv"]
};
```

4. Save the file and reopen it in your browser

### Transaction Format

Each transaction needs:

| Field | Type | Description |
|---|---|---|
| `date` | String | `YYYY-MM-DD` format |
| `month` | String | `YYYY-MM` format (must match a month in the `months` array) |
| `description` | String | What the transaction was for |
| `amount` | Number | Positive for income, negative for expenses |
| `category` | String | One of your budget categories (or any custom name) |
| `status` | String | `""` (empty), `"could cancel"`, or `"canceled"` |
| `source` | String | Where the data came from (for reference) |
| `id` | String | Unique identifier for each transaction |

### Categories

The dashboard works with any categories you define. The sample uses Ghana-specific ones:

- **Income** — Salary, deposits, refunds
- **Groceries** — Food and household supplies
- **Transportation** — Bolt, trotro, fuel, parking
- **Utilities** — ECG, water, airtime, internet
- **Dining** — Restaurants, waakye, kelewele, food delivery
- **Entertainment** — Netflix, Spotify, events
- **Health** — Pharmacy, hospital, insurance
- **Personal Care** — Barber, cosmetics, clothing
- **Transfer** — Savings transfers, mobile money cash-out
- **Housing** — Rent, mortgage, maintenance

Add or remove categories by editing the `budgets` object and your transaction `category` fields.

### Budgets

Set monthly spending targets in the `budgets` object:

```javascript
"budgets": {
  "Groceries": 800,
  "Transportation": 300,
  "Utilities": 250,
  "Dining": 200,
  "Entertainment": 100
}
```

The Budget tab shows how you're tracking against each target.

### Savings Streak

The dashboard tracks how many consecutive months you've saved money. It uses `localStorage` in your browser, so the streak persists between sessions.

### Exporting Data

In the Transactions tab, click **"Refresh & Export overrides"** to download a CSV of your transaction status marks. You can reimport this data later.

## Ghana-Specific Features

- **GHS currency** — Pre-configured for Ghana Cedi
- **Mobile money keywords** — Recognizes Momo, e-zwich, GIPSS
- **Local merchants** — Shoprite, Melcom, Maxmart, Koala, Papaye, Fan Milk, Cold Store
- **Transport** — Bolt, Yango, Trotro, STC, VIP Bus
- **Utilities** — ECG, Ghana Water, MTN, Vodafone, AirtelTigo, Telecel
- **Food** — Waakye, Kelewele, Jollof, Chop Bar, KFC, Chicken Inn, Pizza Inn
- **GSE stocks** — Full Ghana Stock Exchange listings with prices, yields, and market caps

## Tech Stack

- **Pure HTML/CSS/JavaScript** — No frameworks, no dependencies
- **Canvas API** — For charts and graphs
- **localStorage** — For theme preference and savings streak
- **Single file** — Everything is in one `.html` file

## Browser Support

- Chrome 90+
- Firefox 88+
- Edge 90+
- Safari 14+
- Mobile browsers (responsive design)

## License

MIT — Use it, modify it, share it. No attribution required.

## Contributing

Found a bug or want to add a feature? Open an issue or submit a pull request.

---

**Disclaimer:** This tool is for personal finance tracking only. It does not provide financial advice. Always consult a qualified financial advisor for investment decisions.
