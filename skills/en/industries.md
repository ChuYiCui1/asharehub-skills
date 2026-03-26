# Industry Classification — Shenwan Industries

## SDK Method

```python
client.industry_list(ts_code=None, limit=100, offset=0)
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Stock ticker |
| `name` | Stock name |
| `l1_code` | L1 industry code |
| `l1_name` | L1 industry name (31 industries) |
| `l2_code` | L2 industry code |
| `l2_name` | L2 industry name |
| `l3_code` | L3 industry code |
| `l3_name` | L3 industry name |

## Data Coverage

- Static reference data (SW2021 standard)
- Records: 5,820 stocks across 31 L1 industries
- API path: `GET /v1/reference/industries`
