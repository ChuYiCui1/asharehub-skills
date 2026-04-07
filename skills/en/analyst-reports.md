# Analyst Reports — Sell-Side Earnings Forecasts

## SDK Method

```python
client.analyst_reports(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 23 columns. Numeric fields are `float64`. Returns empty DataFrame if no data.

## Example

```python
df = client.analyst_reports(ts_code="600519.SH", limit=5)
print(df[["report_date", "org_name", "rating", "max_price", "eps"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Report start date, YYYY-MM-DD |
| `end_date` | str | None | Report end date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 3000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

ts_code, name, report_date, report_title, org_name (brokerage), author_name, quarter (forecast period), op_rt/op_pr/tp/np (revenue/profit forecasts), eps, pe, roe, ev_ebitda, rating (buy/hold/sell), max_price, min_price, imp_dg.

## Data Coverage

- From: 2010+
- Useful for tracking analyst consensus and price targets
- API path: `GET /v1/financials/analyst-reports`
