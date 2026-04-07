# Southbound Holdings — Mainland-Held HK Stocks

## Background — Mainland Capital in HK Stocks

This endpoint is the **mirror image of northbound holdings**. It tracks how much of each Hong Kong-listed stock is held by mainland Chinese investors via the Stock Connect.

### Why this matters
- **"Southbound favored" stocks**: When mainland investors heavily accumulate a HK-listed stock, it's a sign of mainland conviction — often Tencent, Meituan, BYD, internet platforms, or HK-listed Chinese banks.
- **HK price discovery shifted to mainland**: For dual-listed companies (HK + A-share), heavy mainland ownership of the HK shares means HK pricing is increasingly driven by mainland sentiment.
- **A/H premium signals**: When `ratio` rises sharply, the HK-A premium often narrows (mainland investors arbitraging the discount).

### Key fields explained
- **`ts_code`**: HK stock code (e.g. "00700" for Tencent).
- **`vol`**: Shares held by mainland investors (in shares).
- **`ratio`**: As % of total shares outstanding.
- **`exchange`**: SH or SZ — which connect channel was used.

### Caveats
- HK stock codes use HK format, not A-share format.
- Includes both H-shares (mainland incorporated, HK listed) and red chips (HK incorporated subsidiaries of mainland firms).
- Mainland mutual funds and individual investors can both use southbound; this is the aggregate.

## SDK Method

```python
client.southbound_holdings(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 6 columns. Returns empty DataFrame if no data.

## Example

```python
df = client.southbound_holdings(limit=5)
print(df[["trade_date", "ts_code", "name", "vol", "ratio"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | HK stock code |
| `start_date` | str | None | Start date YYYY-MM-DD |
| `end_date` | str | None | End date YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

trade_date, ts_code (HK), name, vol (shares held by mainland), ratio (% of total shares), exchange (SH or SZ channel).

## Data Coverage

- From: 2020-01-02
- Mirror of northbound-holdings: tracks mainland investor positions in HK stocks
- API path: `GET /v1/flows/southbound-holdings`
