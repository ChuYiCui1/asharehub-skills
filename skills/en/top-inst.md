# Top Inst — Dragon & Tiger Institutional Seats

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
