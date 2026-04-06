# Income Statement

## SDK Method

```python
client.income(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, ann_date, end_date, revenue, n_income, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.income(ts_code="000001.SZ", limit=3)
print(df[["end_date", "revenue", "n_income"]])
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
| **Revenue** | `total_revenue`, `revenue` |
| **Costs** | `total_cogs`, `oper_cost`, `sell_exp`, `admin_exp`, `fin_exp`, `rd_exp` |
| **Profit** | `operate_profit`, `total_profit`, `n_income`, `n_income_attr_p` |
| **Non-operating** | `non_oper_income`, `non_oper_exp` |
| **Per-share** | `basic_eps`, `diluted_eps` |
| **Other** | `income_tax`, `ebit`, `ebitda` |
| **Dates** | `ann_date`, `f_ann_date`, `end_date` |
| **Meta** | `report_type`, `comp_type`, `update_flag` |

## Notes

- All monetary values in CNY
- `end_date` = fiscal period (e.g. 2024-12-31 for annual, 2024-06-30 for H1)
- API path: `GET /v1/financials/income`
