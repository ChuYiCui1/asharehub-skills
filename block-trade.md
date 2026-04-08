# Block Trade — Off-Exchange Large Deals

## SDK Method

```python
client.block_trade(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, trade_date, price, vol, amount, buyer, seller. Returns empty DataFrame if no data.

## Example

```python
df = client.block_trade(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "price", "vol", "buyer", "seller"]])
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
| `trade_date` | Trading date |
| `price` | Trade price (CNY) |
| `vol` | Volume (10k shares) |
| `amount` | Amount (10k CNY) |
| `buyer` | Buyer broker name |
| `seller` | Seller broker name |

## Data Coverage

- From: 2010-01-04
- Large institutional transactions above regular trading limits
- API path: `GET /v1/market/block-trade`
