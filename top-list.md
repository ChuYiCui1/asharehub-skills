# Top List — Dragon & Tiger List

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
