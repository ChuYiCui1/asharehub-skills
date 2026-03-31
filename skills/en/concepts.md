# Concepts — Theme/Concept Sector Indices

## SDK Method

```python
client.concepts(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, trade_date, name, pct_change, leading, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.concepts(limit=3)
print(df[["trade_date", "name", "pct_change", "leading"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Concept code, e.g. `BK0425.DC` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Concept index code (e.g. BK0425.DC) |
| `trade_date` | Trading date |
| `name` | Concept name (e.g. AI, New Energy, Semiconductors) |
| `leading` | Leading stock name |
| `leading_code` | Leading stock code |
| `pct_change` | Daily return % |
| `leading_pct` | Leading stock return % |
| `total_mv` | Total market value (10k CNY) |
| `turnover_rate` | Turnover rate % |
| `up_num` | Number of rising stocks |
| `down_num` | Number of falling stocks |
| `idx_type` | Index type |
| `level` | Index level |

## Data Coverage

- From: 2025-04-01
- Records: 109K+, 508 concept indices
- API path: `GET /v1/market/concepts`
