# 涨跌停统计

## SDK 方法

```python
client.limit_list(ts_code=None, start_date=None, end_date=None, limit_type=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.limit_list(limit=3, limit_type="U")
print(df[["trade_date", "ts_code", "name", "pct_chg"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit_type` | str | None | `U`=涨停，`D`=跌停，`Z`=炸板 |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `trade_date` | 交易日期 |
| `ts_code` / `name` | 股票代码 / 名称 |
| `close` / `pct_chg` | 收盘价 / 涨跌幅 |
| `first_time` / `last_time` | 首次/最后封板时间 |
| `open_times` | 开板次数 |
| `limit_times` | 连板天数 |
| `limit` | 类型：U=涨停，D=跌停，Z=炸板 |

## 数据范围

- 起始日期：2020 年起
- 不含 ST 股
- API 路径：`GET /v1/market/limit-list`
