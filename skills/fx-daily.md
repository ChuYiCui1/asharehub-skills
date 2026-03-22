# FX Daily — Foreign Exchange Rates

## SDK Method

```python
client.fx_daily(ts_code="USDCNH.FXCM", start_date=None, end_date=None, limit=100, offset=0)
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | `USDCNH.FXCM` | FX pair code |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 2000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | FX pair code |
| `trade_date` | Trading date |
| `bid_open`, `bid_close`, `bid_high`, `bid_low` | Bid OHLC prices |
| `ask_open`, `ask_close`, `ask_high`, `ask_low` | Ask OHLC prices |
| `tick_qty` | Number of quote ticks |

## Data Coverage

- From: 2012-01-01
- Default pair: USDCNH (USD vs offshore CNY)
- Rising USDCNH = CNY weakening, typically pressures foreign inflows into A-shares
- API path: `GET /v1/fx/daily`
