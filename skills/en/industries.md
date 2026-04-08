# Industry Classification — Shenwan Industries

## SDK Method

```python
client.industry_list(ts_code=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, name, l1_code, l1_name, l2_code, l2_name, l3_code, l3_name. Returns empty DataFrame if no data.

## Example

```python
df = client.industry_list(ts_code="000001.SZ")
print(df[["ts_code", "l1_name", "l2_name", "l3_name"]])
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
- API path: `GET /v1/reference/industries`
