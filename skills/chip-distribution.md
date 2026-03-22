# Chip Distribution — Cost Basis & Winner Rate

## SDK Method

```python
client.chip_distribution(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
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
| `ts_code`, `trade_date` | Stock code and date |
| `his_low`, `his_high` | Historical price extremes (CNY) |
| `cost_5pct` | 5th percentile cost basis (CNY) |
| `cost_15pct` | 15th percentile cost basis (CNY) |
| `cost_50pct` | Median cost basis (CNY) |
| `cost_85pct` | 85th percentile cost basis (CNY) |
| `cost_95pct` | 95th percentile cost basis (CNY) |
| `weight_avg` | Weighted average cost of all holders (CNY) |
| `winner_rate` | % of holders in profit (0-100). Values > 80 suggest strong bullish momentum |

## Data Coverage

- From: 2020-01-02
- Records: 7.3M+
- China-specific metric for analyzing shareholder cost structure
- API path: `GET /v1/chips/distribution`
