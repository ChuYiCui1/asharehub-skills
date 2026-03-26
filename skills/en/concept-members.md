# Concept Members — Concept Index Constituents

## SDK Method

```python
client.concept_members(ts_code=None, con_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Concept index code, e.g. `BK0425.DC` |
| `con_code` | str | None | Stock code filter, e.g. `000001.SZ` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `ts_code` | Concept index code |
| `con_code` | Constituent stock code |
| `name` | Stock name |

## Data Coverage

- From: 2025-04-28
- Records: 678K+
- Use concepts endpoint first to find concept codes, then query members here
- API path: `GET /v1/market/concept-members`
