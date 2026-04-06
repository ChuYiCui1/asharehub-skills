# Adjustment Factor — Forward/Backward Price Restoration

## SDK Method

```python
client.adj_factor(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, trade_date, adj_factor. Returns empty DataFrame if no data.

## Example

```python
df = client.adj_factor(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "adj_factor"]])
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
| `ts_code` | Stock code |
| `trade_date` | Trading date |
| `adj_factor` | Adjustment factor |

## Notes

- Forward adjusted price = unadjusted price * adj_factor / latest adj_factor
- Backward adjusted price = unadjusted price * adj_factor
- API path: `GET /v1/market/adj-factor`
