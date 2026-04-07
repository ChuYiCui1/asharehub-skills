# 龙虎榜机构明细

## SDK 方法

```python
client.top_inst(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 10 列，数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.top_inst(limit=5)
print(df[["trade_date", "ts_code", "exalter", "net_buy", "reason"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 起始日期 YYYY-MM-DD |
| `end_date` | str | None | 结束日期 YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

trade_date、ts_code、exalter(机构席位名称)、buy/buy_rate(买入额/占比)、sell/sell_rate(卖出额/占比)、net_buy(净买入)、side(买卖方向)、reason(上榜原因)。

## 数据范围

- 起始日期：2020-01-02
- 每只龙虎榜股票的机构席位明细
- API 路径：`GET /v1/market/top-inst`
