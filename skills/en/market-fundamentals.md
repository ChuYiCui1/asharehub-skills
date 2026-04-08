# Market Fundamentals — Daily Valuation Metrics

## SDK Method

```python
client.fundamentals(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, trade_date, pe, pe_ttm, pb, total_mv, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.fundamentals(ts_code="600519.SH", limit=3)
print(df[["trade_date", "pe_ttm", "pb", "total_mv"]])
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
| `close` | Closing price |
| `turnover_rate`, `turnover_rate_f` | Turnover rates % |
| `volume_ratio` | Volume ratio (today avg / 5-day avg) |
| `pe`, `pe_ttm` | Price-to-Earnings ratios |
| `pb` | Price-to-Book ratio |
| `ps`, `ps_ttm` | Price-to-Sales ratios |
| `dv_ratio`, `dv_ttm` | Dividend yields % |
| `total_share`, `float_share`, `free_share` | Share counts (10k shares) |
| `total_mv`, `circ_mv` | Total / circulating market cap (10k CNY) |

## Data Coverage

- From: 2010-01-04
- API path: `GET /v1/market/fundamentals`
