# Top Inst — Dragon & Tiger Institutional Seats

## Background — Granular Seat-Level Detail

This endpoint returns the **per-seat breakdown** of institutional buying/selling for stocks on the Dragon & Tiger list. While `top_list` aggregates the institutional totals, this endpoint shows **which specific brokerage branches** were buying or selling.

### Why this is uniquely valuable in China
- Chinese exchanges require disclosure down to the **brokerage branch level** (营业部), not just the firm. So you see "中信建投上海溧阳路" rather than just "CITIC".
- Famous "hot money" branches have nicknames in retail communities (e.g. "炒股养家", "孙哥") and their activity is closely tracked.
- **Seat continuity** is a strong signal: if the same branch repeatedly appears on the buy side of a stock over multiple days, it implies a single trader is accumulating.

### Key fields explained
- **`exalter`**: The brokerage branch name (in Chinese). Format is usually "Brokerage + Branch", e.g. "国泰君安证券股份有限公司上海江苏路证券营业部".
- **`buy` / `sell`**: Buy/sell amounts from this single seat (CNY).
- **`buy_rate` / `sell_rate`**: This seat's contribution as % of the stock's total turnover that day.
- **`net_buy`**: `buy - sell`. Positive = net accumulator, negative = net distributor.
- **`side`**: Whether this row represents a buy-side or sell-side disclosure.
- **`reason`**: Why the stock was on the Dragon & Tiger list (e.g. "日涨幅偏离值达7%" / "Daily price change ≥7%").

### Investment use cases
- **Hot money tracking**: Build a watchlist of known "smart money" seats and alert when they appear on a stock.
- **Coordinated activity detection**: Multiple known seats on the same side of a stock = potential coordinated trade.
- **Distribution detection**: Same seat that bought 3 days ago now selling = profit-taking signal.

### Caveats
- Branch names are in Chinese; you may need a mapping table to identify famous "hot money" seats.
- A single trader can use multiple branches to obscure their footprint.
- Branches don't represent funds; they aggregate all clients trading through that physical office.

## SDK Method

```python
client.top_inst(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 10 columns. Numeric fields are `float64`. Returns empty DataFrame if no data.

## Example

```python
df = client.top_inst(limit=5)
print(df[["trade_date", "ts_code", "exalter", "net_buy", "reason"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code |
| `start_date` | str | None | Start date YYYY-MM-DD |
| `end_date` | str | None | End date YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

trade_date, ts_code, exalter (institutional seat name), buy/buy_rate, sell/sell_rate, net_buy, side, reason.

## Data Coverage

- From: 2020-01-02
- Granular institutional seat detail per stock per day
- API path: `GET /v1/market/top-inst`
