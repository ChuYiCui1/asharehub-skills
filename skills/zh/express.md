# 业绩快报

## SDK 方法

```python
client.express(ts_code=None, start_date=None, end_date=None, limit=50, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.express(ts_code="000001.SZ", limit=3)
print(df[["ann_date", "end_date", "revenue", "n_income", "diluted_roe"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 公告起始日期，YYYY-MM-DD |
| `end_date` | str | None | 公告截止日期，YYYY-MM-DD |
| `limit` | int | 50 | 返回行数，最大 1000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 股票代码 |
| `ann_date` / `end_date` | 公告日期 / 报告期 |
| `revenue` / `n_income` | 营业收入 / 净利润（元） |
| `diluted_eps` / `diluted_roe` | 摊薄每股收益 / 摊薄 ROE |
| `yoy_net_profit` | 净利润同比增长率 % |
| `bps` | 每股净资产（元） |
| `perf_summary` | 业绩说明 |

## 备注

- 业绩快报在正式财报之前披露
- API 路径：`GET /v1/financials/express`
