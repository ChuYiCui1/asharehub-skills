# Audit Opinions — Annual Report Audit Results

## SDK Method

```python
client.audit(ts_code=None, start_date=None, end_date=None, limit=50, offset=0)
```

## Returns

`pd.DataFrame` — 7 columns. Returns empty DataFrame if no data.

## Example

```python
df = client.audit(ts_code="000001.SZ", limit=3)
print(df[["end_date", "audit_result", "audit_agency", "audit_fees"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code |
| `start_date` | str | None | Period start YYYY-MM-DD |
| `end_date` | str | None | Period end YYYY-MM-DD |
| `limit` | int | 50 | Max rows, up to 1000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

ts_code, ann_date, end_date, audit_result (opinion type), audit_fees, audit_agency (firm name), audit_sign (signing auditors).

## Data Coverage

- From: 2006-04-20
- Annual data only (released with annual reports)
- API path: `GET /v1/financials/audit`
