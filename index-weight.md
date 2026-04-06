# Index Weight — Constituent Weights

## SDK Method

```python
client.index_weight(index_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: index_code, trade_date, con_code, con_name, weight. Returns empty DataFrame if no data.

## Example

```python
df = client.index_weight(index_code="399300.SZ", limit=5)
print(df[["con_code", "con_name", "weight"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `index_code` | str | None | Index code, e.g. `399300.SZ` (CSI 300) |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `index_code` | Index code |
| `trade_date` | Effective date |
| `con_code` | Constituent stock code |
| `con_name` | Constituent stock name |
| `weight` | Weight in index % |

## Common Index Codes

| Code | Name |
|------|------|
| `399300.SZ` | CSI 300 |
| `000905.SH` | CSI 500 |
| `000016.SH` | SSE 50 |

## Notes

- Rebalanced periodically (semi-annual for major indices)
- API path: `GET /v1/indices/index-weight`
