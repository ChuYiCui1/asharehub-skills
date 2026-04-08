# Northbound Holdings — Foreign Investor Stock Holdings

## Background — Tracking Foreign Investor Positions

This endpoint shows **foreign investor holdings of A-share stocks** at the individual stock level. While `moneyflow_hsgt` shows daily aggregate flows, this shows **who owns what**.

### Why this matters for global investors
- **The cleanest view of foreign positioning in A-shares**: Shows which specific A-share stocks foreigners hold and how heavily.
- **Stock-level conviction signal**: Stocks with high foreign ownership ratios (>5% of free float) often signal foreign-favored "core holdings" — typically large-cap, liquid, high-quality companies.
- **Style indicator**: Foreign holdings concentration in consumer staples, premium liquor (e.g. Kweichow Moutai), and large-cap banks reveals foreign preference for "quality" factors over speculative growth.

### Key fields explained
- **`vol`**: Number of shares held by all foreign investors via Stock Connect (in shares).
- **`ratio`**: Foreign ownership as % of total shares outstanding. >5% is considered heavy foreign exposure for A-shares.
- **`exchange`**: SH or SZ — which connect channel was used to acquire the position.

### Investment use cases
- **Foreign favorite screening**: Filter stocks where `ratio > 5` and rising over time = foreign accumulation.
- **Risk-off detection**: Sharp decline in `vol` for typical "foreign favorites" (Moutai, Ping An, CATL) often precedes broader risk-off in A-shares.
- **Comparison with index weights**: Stocks where foreign ownership >> their MSCI China weight may be over-positioned and vulnerable to outflows.

### Caveats
- Only includes positions held via Stock Connect, not QFII (qualified foreign institutional investor) positions held directly through other channels.
- For unlisted-on-connect stocks, foreign holdings = 0 even if some QFII exposure exists.
- Foreign ownership has legal caps (typically 30% per stock). When approaching the cap, new buys may be restricted.


## SDK Method

```python
client.northbound_holdings(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, ts_code, name, vol, ratio, exchange. Returns empty DataFrame if no data.

## Example

```python
df = client.northbound_holdings(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "name", "vol", "ratio"]])
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
| `name` | Stock name (Chinese) |
| `vol` | Shares held by northbound investors |
| `ratio` | Holding ratio (% of total shares) |
| `exchange` | Exchange (SH/SZ) |

## Data Coverage

- From: 2020-01-02
- Key signal for foreign investor positioning
- API path: `GET /v1/flows/moneyflow-hsgt-holdings`
