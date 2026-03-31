# Cash Flow Statement

## SDK Method

```python
client.cash_flow(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, ann_date, end_date, n_cashflow_act, free_cashflow, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.cash_flow(ts_code="000001.SZ", limit=3)
print(df[["end_date", "n_cashflow_act", "free_cashflow"]])
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
| **Operating** | `c_fr_sale_sg`, `c_pay_goods_purch_serv_rec`, `n_cashflow_act` |
| **Investing** | `c_pay_acq_const_fix_intang_oasset`, `c_fr_disp_fix_intang_oasset`, `n_cashflow_inv_act` |
| **Financing** | `c_fr_borr`, `c_pay_dist_dpcp_int_exp`, `n_cash_flows_fnc_act` |
| **Summary** | `n_incr_cash_cash_equ`, `c_cash_equ_beg_period`, `c_cash_equ_end_period` |
| **Derived** | `free_cashflow` (= operating cash flow - capex) |

## Notes

- All monetary values in CNY
- API path: `GET /v1/financials/cash-flow`
