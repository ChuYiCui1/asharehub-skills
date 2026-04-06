# 沪深港通资金

## SDK 方法

```python
client.moneyflow_hsgt(start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.moneyflow_hsgt(limit=3)
print(df[["trade_date", "north_money", "south_money"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 2000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `trade_date` | 交易日期 |
| `hgt_ss`, `hgt_sz` | 沪股通/深股通北向（百万元） |
| `ggt_ss`, `ggt_sz` | 港股通南向（百万元） |
| `north_money` | 北向资金净流入合计（百万元），正值=外资净买入 |
| `south_money` | 南向资金净流入合计（百万元） |

## 数据范围

- 起始日期：2014-11-17
- 每个交易日一条记录
- 外资对 A 股情绪的关键指标
- API 路径：`GET /v1/flows/moneyflow-hsgt`
