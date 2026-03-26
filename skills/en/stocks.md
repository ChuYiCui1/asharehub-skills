# Stock List — A-Share Stock Reference

## SDK Method

```python
client.stock_list(ts_code=None, limit=100, offset=0)
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Stock ticker (e.g. 000001.SZ) |
| `symbol` | Ticker symbol (e.g. 000001) |
| `name` | Stock name (Chinese) |
| `area` | Province/city |
| `industry` | Industry |
| `fullname` | Full company name (Chinese) |
| `enname` | English company name |
| `cnspell` | Pinyin abbreviation |
| `market` | Market: 主板/创业板/科创板/北交所 |
| `exchange` | Exchange: SSE/SZSE/BSE |
| `curr_type` | Currency type |
| `list_status` | L=listed, D=delisted, P=paused |
| `list_date` | IPO date |
| `delist_date` | Delist date |
| `is_hs` | Stock Connect eligible: H/S/N |

## Data Coverage

- Static reference data
- Records: 5,491 stocks
- API path: `GET /v1/reference/stocks`
