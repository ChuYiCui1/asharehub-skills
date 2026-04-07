# Technical Factors Pro — Professional Indicators (200+)

## SDK Method

```python
client.technical_factors_pro(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — 200+ columns. Numeric fields are `float64`. Returns empty DataFrame if no data.

## Example

```python
df = client.technical_factors_pro(ts_code="000001.SZ", limit=1)
print(df[["trade_date", "close_qfq", "macd_qfq", "rsi_6_qfq", "ma20_qfq"]])
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

200+ columns: OHLCV, valuation (PE/PB/PS/MV), and technical indicators (MA, EMA, MACD, KDJ, RSI, BOLL, CCI, ATR, BBI, BIAS, BRAR, CR, DFMA, DMI, DPO, EMV, EXPMA, Keltner, MASS, MFI, MTM, OBV, PSY, ROC, TRIX, VR, W&R, ASI, TAQ, XSII). Each technical indicator has `_bfq` (unadjusted), `_qfq` (forward-adjusted), `_hfq` (backward-adjusted) variants.

## Data Coverage

- From: 2020-01-02
- Records: 11M+
- API path: `GET /v1/market/technical-factors-pro`
