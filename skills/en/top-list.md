# Top List — Dragon & Tiger List

## Background — China's Unique Disclosure Mechanism

**The "Dragon & Tiger List" (龙虎榜)** is a unique disclosure system in China. When a stock has unusual price movement or trading volume, the Shanghai/Shenzhen exchanges require disclosure of the **top 5 brokerage seats** by buy and sell volume.

### When does a stock land on the list?
A stock gets disclosed if it triggers any of:
- Daily price change ≥ ±7% (≥ ±15% for ChiNext/STAR)
- Daily turnover rate ≥ 20%
- Daily price range ≥ 15%
- Several consecutive limit-up/down days
- Other unusual activity flagged by exchanges

### Why investors track this
- **Institutional footprint**: The disclosed seats often include well-known "hot money" hubs (游资席位) in Shanghai/Shenzhen and famous private fund seats. Tracking which seats are buying/selling is a major retail strategy.
- **Coordinated buying signal**: When multiple known institutional seats appear on the buy side simultaneously, it's interpreted as collective interest.
- **Pump-and-dump warning**: A stock with one large buy seat followed by the same seat selling within days is a classic pump-and-dump pattern.

### Key fields explained
- **`l_buy` / `l_sell` / `l_amount` (CNY)**: Total buy/sell amounts from the disclosed institutional seats.
- The actual seat-level detail (which broker branch) is in `top_inst` — see that endpoint for institutional breakdown.

### Caveats
- Only the top 5 seats by volume are disclosed; smaller participants are aggregated as "other".
- "Institutional seat" doesn't always mean institution — it can be a famous retail aggregator or hot-money trader operating through that branch.

## SDK Method

```python
client.top_list(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, ts_code, name, close, pct_change, amount, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.top_list(limit=3)
print(df[["trade_date", "ts_code", "name", "pct_change"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `ts_code` | Stock code |
| `name` | Stock name |
| `close` | Closing price (CNY) |
| `pct_change` | Price change % |
| `turnover_rate` | Turnover rate % |
| `amount` | Total turnover (CNY) |
| `l_sell` | Listed institutional sell amount (CNY) |
| `l_buy` | Listed institutional buy amount (CNY) |
| `l_amount` | Listed institutional total amount (CNY) |

## Data Coverage

- From: 2024-01-02
- Records: 35K+
- Stocks triggering exchange disclosure due to unusual price/volume
- API path: `GET /v1/market/top-list`
