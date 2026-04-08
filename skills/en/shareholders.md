# Shareholders — Shareholder Count

## SDK Method

```python
client.shareholders(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, ann_date, end_date, holder_num. Returns empty DataFrame if no data.

## Example

```python
df = client.shareholders(ts_code="000001.SZ", limit=3)
print(df[["end_date", "holder_num"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Report period start, YYYY-MM-DD |
| `end_date` | str | None | Report period end, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Stock code |
| `ann_date` | Announcement date |
| `end_date` | Report period end date |
| `holder_num` | Number of shareholders |

## Data Coverage

- From: 2024-04-01
- Quarterly reports. Declining count = chip concentration (accumulation by large holders)
- API path: `GET /v1/market/shareholders`
