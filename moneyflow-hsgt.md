# HSGT Capital Flows — Stock Connect Capital Flows

## Background — China's Cross-Border Connect

**Stock Connect (沪深港通, "HSGT")** is the primary channel through which foreign investors can trade Chinese A-shares and mainland investors can trade HK stocks. Launched in 2014 (Shanghai-HK) and 2016 (Shenzhen-HK).

### Two directions
- **Northbound (北向, "north money")**: Foreign capital flowing INTO A-shares. **This is the most-watched indicator of foreign sentiment toward Chinese equities.**
- **Southbound (南向, "south money")**: Mainland Chinese capital flowing INTO HK stocks.

### Why this is critical for global investors
- **Northbound is the foreign investor pulse**: When `north_money` is consistently positive over weeks, it signals foreign accumulation. Persistent outflows often precede broader index weakness.
- **Real-time policy signal**: Daily flows respond quickly to policy changes (regulatory, tax, geopolitical). Watch for sudden reversals.
- **No other clean proxy exists**: Unlike US markets where 13F filings show institutional positions, China's foreign flows are best measured here.

### Key fields explained
All values in **millions of CNY (百万元)**:
- **`north_money`**: Total net inflow from foreign investors via both Shanghai and Shenzhen connects. Positive = net buying.
- **`south_money`**: Total net inflow from mainland investors into HK stocks. Positive = net buying of HK.
- **`hgt_ss`**: Shanghai-HK connect, northbound (foreign → SSE-listed stocks).
- **`hgt_sz`**: Shenzhen-HK connect, northbound (foreign → SZSE-listed stocks).
- **`ggt_ss`**: HK-Shanghai connect, southbound (mainland → HK via Shanghai).
- **`ggt_sz`**: HK-Shenzhen connect, southbound (mainland → HK via Shenzhen).

### Caveats
- This is **aggregate** data; per-stock holdings are in `northbound_holdings` / `southbound_holdings`.
- Daily flows are noisy — look at 5-day or 20-day rolling averages for trends.
- Connect quotas (daily caps) exist but are rarely hit nowadays.
- During Chinese national holidays, the connect may be partially suspended even if HK is open.


## SDK Method

```python
client.moneyflow_hsgt(start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, hgt_ss, hgt_sz, ggt_ss, ggt_sz, north_money, south_money. Returns empty DataFrame if no data.

## Example

```python
df = client.moneyflow_hsgt(limit=3)
print(df[["trade_date", "north_money", "south_money"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 2000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `hgt_ss`, `hgt_sz` | Shanghai / Shenzhen northbound (millions CNY) |
| `ggt_ss`, `ggt_sz` | HK southbound via Shanghai / Shenzhen (millions CNY) |
| `north_money` | Total northbound net inflow (millions CNY) — positive = net buying |
| `south_money` | Total southbound net inflow (millions CNY) |

## Data Coverage

- From: 2014-11-17
- One record per trading day
- Key indicator of foreign investor sentiment toward A-shares
- API path: `GET /v1/flows/moneyflow-hsgt`
