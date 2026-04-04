# 指数日线

## SDK 方法

```python
client.index_daily(ts_code="000001.SH", start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.index_daily(ts_code="000001.SH", limit=3)
print(df[["trade_date", "close", "pct_chg"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | `000001.SH` | 指数代码 |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 2000 |
| `offset` | int | 0 | 分页偏移量 |

## 常用指数代码

| 代码 | 名称 |
|------|------|
| `000001.SH` | 上证综指 |
| `000300.SH` | 沪深300 |
| `399001.SZ` | 深证成指 |
| `399006.SZ` | 创业板指 |
| `000016.SH` | 上证50 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 指数代码 |
| `trade_date` | 交易日期 |
| `open`, `high`, `low`, `close` | 指数点位 |
| `pre_close` | 昨收 |
| `change` | 涨跌点 |
| `pct_chg` | 涨跌幅 % |
| `vol` | 成交量（手） |
| `amount` | 成交额（千元） |

## 数据范围

- 起始日期：2010-01-04
- API 路径：`GET /v1/indices/daily`
