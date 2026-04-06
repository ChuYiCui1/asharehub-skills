# Balance Sheet

## SDK Method

```python
client.balance_sheet(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, ann_date, end_date, total_assets, total_liab, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.balance_sheet(ts_code="000001.SZ", limit=3)
print(df[["end_date", "total_assets", "total_liab"]])
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
| **Current assets** | `total_cur_assets`, `money_cap`, `notes_receiv`, `accounts_receiv`, `inventories` |
| **Non-current assets** | `total_nca`, `lt_eqt_invest`, `fix_assets`, `cip`, `intan_assets`, `goodwill` |
| **Total** | `total_assets` |
| **Current liabilities** | `total_cur_liab`, `st_borr`, `notes_payable`, `acct_payable` |
| **Non-current liabilities** | `total_ncl`, `lt_borr`, `bond_payable` |
| **Total liabilities** | `total_liab` |
| **Equity** | `total_hldr_eqy_exc_min_int`, `total_hldr_eqy_inc_min_int`, `minority_int` |

## Notes

- All monetary values in CNY
- API path: `GET /v1/financials/balance-sheet`
