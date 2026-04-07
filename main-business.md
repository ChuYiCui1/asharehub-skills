# Main Business Composition

## SDK Method

```python
client.main_business(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 7 columns. Numeric fields are `float64`. Returns empty DataFrame if no data.

## Example

```python
df = client.main_business(ts_code="600519.SH", limit=10)
print(df[["end_date", "bz_item", "bz_sales", "bz_profit"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code |
| `start_date` | str | None | Period start YYYY-MM-DD |
| `end_date` | str | None | Period end YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 2000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

ts_code, end_date, bz_item (segment name), bz_sales (segment revenue), bz_profit, bz_cost, curr_type.

## Data Coverage

- From: 2014-12-31
- Records: 450k+
- Use to understand which products/regions drive a company's business
- API path: `GET /v1/financials/main-business`
