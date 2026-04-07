# 主营业务构成

## SDK 方法

```python
client.main_business(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 7 列，数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.main_business(ts_code="600519.SH", limit=10)
print(df[["end_date", "bz_item", "bz_sales", "bz_profit"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 起始日期 YYYY-MM-DD |
| `end_date` | str | None | 结束日期 YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 2000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

ts_code、end_date、bz_item(业务名称)、bz_sales(业务收入)、bz_profit(业务利润)、bz_cost(业务成本)、curr_type(币种)。

## 数据范围

- 起始日期：2014-12-31
- 记录数：45万+
- 用于了解公司业务构成（按产品/地区）
- API 路径：`GET /v1/financials/main-business`
