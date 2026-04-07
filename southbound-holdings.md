# Southbound Holdings — Mainland-Held HK Stocks

## SDK Method

```python
client.southbound_holdings(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 6 columns. Returns empty DataFrame if no data.

## Example

```python
df = client.southbound_holdings(limit=5)
print(df[["trade_date", "ts_code", "name", "vol", "ratio"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | HK stock code |
| `start_date` | str | None | Start date YYYY-MM-DD |
| `end_date` | str | None | End date YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

trade_date, ts_code (HK), name, vol (shares held by mainland), ratio (% of total shares), exchange (SH or SZ channel).

## Data Coverage

- From: 2020-01-02
- Mirror of northbound-holdings: tracks mainland investor positions in HK stocks
- API path: `GET /v1/flows/southbound-holdings`
