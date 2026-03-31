# Margin Trading — Margin & Short Selling Detail

## SDK Method

```python
client.margin(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, ts_code, name, rzye, rqye, rzrqye, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.margin(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "rzye", "rqye", "rzrqye"]])
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
| `rzye` | Margin buy balance (CNY) — total outstanding margin loans |
| `rqye` | Short sell balance (CNY) — total outstanding short positions |
| `rzmre` | Margin buy amount today (CNY) |
| `rqyl` | Short sell volume today (shares) |
| `rzche` | Margin repayment today (CNY) |
| `rqchl` | Short cover volume today (shares) |
| `rqmcl` | Short sell volume today (shares) |
| `rzrqye` | Total margin + short balance (CNY) |

## Data Coverage

- From: 2020-01-02
- Records: 4.6M+
- Rising rzye = bullish leverage; rising rqye = bearish sentiment
- API path: `GET /v1/market/margin`
