# Trade Calendar — Exchange Trading Days

## SDK Method

```python
client.trade_calendar(exchange=None, start_date=None, end_date=None, is_open=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: exchange, cal_date, is_open, pretrade_date. Returns empty DataFrame if no data.

## Example

```python
df = client.trade_calendar(exchange="SSE", start_date="2024-03-25", end_date="2024-03-31")
print(df[["cal_date", "is_open"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `exchange` | str | None | `SSE` (Shanghai) or `SZSE` (Shenzhen) |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `is_open` | int | None | `1`=trading days only, `0`=closed days only |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `exchange` | Exchange code (SSE / SZSE) |
| `cal_date` | Calendar date |
| `is_open` | 1=trading day, 0=closed |
| `pretrade_date` | Previous trading date |

## Notes

- Covers SSE and SZSE exchanges
- Useful for scheduling data pulls and handling holidays
- API path: `GET /v1/reference/trade-calendar`
