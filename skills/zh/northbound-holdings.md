# 北向持股

## SDK 方法

```python
client.northbound_holdings(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.northbound_holdings(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "name", "vol", "ratio"]])
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
| `trade_date` | 交易日期 |
| `ts_code` | 股票代码 |
| `name` | 股票名称 |
| `vol` | 持股数量 |
| `ratio` | 占总股本比例 % |
| `exchange` | 交易所（SH/SZ） |

## 数据范围

- 起始日期：2020-01-02
- 记录数：400万+
- API 路径：`GET /v1/flows/moneyflow-hsgt-holdings`
