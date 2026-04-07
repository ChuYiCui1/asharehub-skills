# 券商盈利预测 — 卖方研报

## SDK 方法

```python
client.analyst_reports(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 23 列，数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.analyst_reports(ts_code="600519.SH", limit=5)
print(df[["report_date", "org_name", "rating", "max_price", "eps"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 起始日期 YYYY-MM-DD |
| `end_date` | str | None | 结束日期 YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 3000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

ts_code、name、report_date、report_title、org_name(券商)、author_name(分析师)、quarter(预测季度)、op_rt/op_pr/tp/np(营收/利润预测)、eps、pe、roe、ev_ebitda、rating(评级)、max_price/min_price(目标价区间)、imp_dg(关注度)。

## 数据范围

- 起始日期：2010 年起
- 用于追踪卖方一致预期和目标价
- API 路径：`GET /v1/financials/analyst-reports`
