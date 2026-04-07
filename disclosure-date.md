# Disclosure Dates — Financial Report Schedule

## SDK Method

```python
client.disclosure_date(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 6 columns. Returns empty DataFrame if no data.

## Example

```python
df = client.disclosure_date(ts_code="000001.SZ", limit=5)
print(df[["end_date", "pre_date", "actual_date"]])
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

ts_code, ann_date (latest announcement), end_date (fiscal period), pre_date (planned date), actual_date (actual disclosure), modify_date.

## Data Coverage

- From: 2001-02-06
- Records: 300k+
- Use to track when companies will release earnings
- API path: `GET /v1/financials/disclosure-date`
