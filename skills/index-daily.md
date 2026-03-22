# Index Daily — Major Market Indices

## SDK Method

```python
client.index_daily(ts_code="000001.SH", start_date=None, end_date=None, limit=100, offset=0)
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | `000001.SH` | Index code |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 2000 |
| `offset` | int | 0 | Pagination offset |

## Common Index Codes

| Code | Name |
|------|------|
| `000001.SH` | SSE Composite |
| `000300.SH` | CSI 300 |
| `399001.SZ` | SZSE Component |
| `399006.SZ` | ChiNext |
| `000016.SH` | SSE 50 |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Index code |
| `trade_date` | Trading date |
| `open`, `high`, `low`, `close` | Index level |
| `pre_close` | Previous close |
| `change` | Point change |
| `pct_chg` | Daily return % |
| `vol` | Volume in lots |
| `amount` | Turnover in thousands of CNY |

## Data Coverage

- From: 2010-01-04
- API path: `GET /v1/indices/daily`
