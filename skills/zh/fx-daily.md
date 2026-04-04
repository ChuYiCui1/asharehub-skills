# 外汇日线

## SDK 方法

```python
client.fx_daily(ts_code="USDCNH.FXCM", start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.fx_daily(ts_code="USDCNH.FXCM", limit=3)
print(df[["trade_date", "bid_close", "ask_close"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | `USDCNH.FXCM` | 外汇对代码 |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 2000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 外汇对代码 |
| `trade_date` | 交易日期 |
| `bid_open`, `bid_close`, `bid_high`, `bid_low` | 买入价 OHLC |
| `ask_open`, `ask_close`, `ask_high`, `ask_low` | 卖出价 OHLC |
| `tick_qty` | 报价笔数 |

## 数据范围

- 起始日期：2012-01-01
- 默认货币对：USDCNH（美元/离岸人民币）
- USDCNH 上涨 = 人民币贬值，通常对 A 股外资流入形成压力
- API 路径：`GET /v1/fx/daily`
