# 技术因子专业版 — 200+ 指标

## SDK 方法

```python
client.technical_factors_pro(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 200+ 列，数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.technical_factors_pro(ts_code="000001.SZ", limit=1)
print(df[["trade_date", "close_qfq", "macd_qfq", "rsi_6_qfq", "ma20_qfq"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码，如 `000001.SZ` |
| `start_date` | str | None | 起始日期 YYYY-MM-DD |
| `end_date` | str | None | 结束日期 YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

200+ 列：OHLCV、估值指标(PE/PB/PS/市值)、以及技术指标(MA/EMA/MACD/KDJ/RSI/BOLL/CCI/ATR/BBI/BIAS/BRAR/CR/DFMA/DMI/DPO/EMV/EXPMA/Keltner/MASS/MFI/MTM/OBV/PSY/ROC/TRIX/VR/W&R/ASI/TAQ/XSII)。每个技术指标都有 `_bfq`(不复权)/`_qfq`(前复权)/`_hfq`(后复权) 三个版本。

## 数据范围

- 起始日期：2020-01-02
- API 路径：`GET /v1/market/technical-factors-pro`
