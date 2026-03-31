# Financial Indicators — Quarterly Financials

## SDK Method

```python
client.financial_indicators(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, ann_date, end_date, roe, eps, netprofit_margin, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.financial_indicators(ts_code="000001.SZ", limit=3)
print(df[["end_date", "roe", "eps", "netprofit_margin"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Report period start, YYYY-MM-DD |
| `end_date` | str | None | Report period end, YYYY-MM-DD |
| `limit` | int | 20 | Max rows, up to 200 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Category | Fields |
|----------|--------|
| **Per-share** | `eps`, `dt_eps`, `total_revenue_ps`, `revenue_ps`, `bps`, `ocfps` |
| **Profitability** | `roe`, `roe_waa`, `roe_dt`, `roa`, `gross_margin`, `netprofit_margin` |
| **Leverage** | `debt_to_assets` |
| **Liquidity** | `current_ratio`, `quick_ratio`, `cash_ratio` |
| **Efficiency** | `assets_turn`, `inv_turn`, `ar_turn` |
| **Returns** | `roic` |
| **Growth** | `basic_eps_yoy`, `dt_eps_yoy`, `netprofit_yoy`, `dt_netprofit_yoy` |
| **R&D** | `rd_exp` (CNY) |
| **Dates** | `ann_date` (announcement date), `end_date` (fiscal period end) |

## Data Coverage

- `end_date` refers to fiscal period end (e.g. `2024-12-31` = annual, `2024-06-30` = semi-annual)
- API path: `GET /v1/financials/indicators`
