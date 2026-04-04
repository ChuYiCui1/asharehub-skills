# 日线行情

## SDK 方法

```python
client.market_daily(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`，可直接运算。无数据时返回空 DataFrame。

## 示例

```python
df = client.market_daily(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "close", "pct_chg"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码，如 `000001.SZ`（平安银行）、`600519.SH`（贵州茅台） |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 股票代码 |
| `trade_date` | 交易日期 |
| `open`, `high`, `low`, `close` | 开高低收价格（元） |
| `pre_close` | 昨收价（除权后） |
| `change` | 涨跌额（元） |
| `pct_chg` | 涨跌幅 % |
| `vol` | 成交量（手，1手=100股） |
| `amount` | 成交额（千元） |

## 数据范围

- 起始日期：2020-01-02
- 记录数：730万+
- API 路径：`GET /v1/market/daily`
