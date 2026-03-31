# Northbound Holdings — Foreign Investor Stock Holdings

## SDK Method

```python
client.northbound_holdings(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, ts_code, name, vol, ratio, exchange. Returns empty DataFrame if no data.

## Example

```python
df = client.northbound_holdings(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "name", "vol", "ratio"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `ts_code` | Stock code |
| `name` | Stock name (Chinese) |
| `vol` | Shares held by northbound investors |
| `ratio` | Holding ratio (% of total shares) |
| `exchange` | Exchange (SH/SZ) |

## Data Coverage

- From: 2020-01-02
- Records: 4M+
- Key signal for foreign investor positioning
- API path: `GET /v1/flows/northbound-holdings`
