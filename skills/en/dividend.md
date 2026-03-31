# Dividend — Cash & Stock Distribution

## SDK Method

```python
client.dividend(ts_code=None, start_date=None, end_date=None, limit=50, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, end_date, ann_date, cash_div, stk_div, ex_date, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.dividend(ts_code="000001.SZ", limit=3)
print(df[["end_date", "cash_div", "stk_div", "ex_date"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Announcement start date, YYYY-MM-DD |
| `end_date` | str | None | Announcement end date, YYYY-MM-DD |
| `limit` | int | 50 | Max rows, up to 1000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Stock code |
| `end_date` | Dividend fiscal year end |
| `ann_date` | Plan announcement date |
| `div_proc` | Progress: 预案/董事会预案/股东大会/实施 |
| `cash_div` | Cash dividend per share pre-tax (CNY) |
| `cash_div_tax` | Cash dividend per share after-tax (CNY) |
| `stk_div` | Total stock dividend per share |
| `stk_bo_rate` | Bonus share rate per share |
| `stk_co_rate` | Share conversion rate per share |
| `record_date` | Record date (股权登记日) |
| `ex_date` | Ex-dividend date (除权除息日) |
| `pay_date` | Payment date |

## Notes

- Buy before `ex_date` to qualify for dividend
- API path: `GET /v1/shareholders/dividend`
