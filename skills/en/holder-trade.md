# Holder Trade — Major Shareholder Trades

## SDK Method

```python
client.holder_trade(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, ann_date, holder_name, in_de, change_vol, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.holder_trade(ts_code="000001.SZ", limit=3)
print(df[["ann_date", "holder_name", "in_de", "change_vol"]])
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
| `ts_code` | Stock code |
| `ann_date` | Announcement date |
| `holder_name` | Shareholder/executive name |
| `holder_type` | G=executive, P=individual, C=company |
| `in_de` | Direction: IN=buy, DE=sell |
| `change_vol` | Number of shares changed |
| `change_ratio` | Change as % of total shares |
| `after_share` | Shares held after change |
| `after_ratio` | Holding ratio after change % |
| `avg_price` | Average transaction price (CNY) |
| `total_share` | Total company shares |
| `begin_date` | Trade period start |
| `close_date` | Trade period end |

## Data Coverage

- From: 2019-11-20
- Key signal for insider sentiment
- API path: `GET /v1/market/holder-trade`
