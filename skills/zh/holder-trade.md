# 股东增减持

## SDK 方法

```python
client.holder_trade(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.holder_trade(ts_code="000001.SZ", limit=3)
print(df[["ann_date", "holder_name", "in_de", "change_vol"]])
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
| `ann_date` | 公告日期 |
| `holder_name` | 股东名称 |
| `holder_type` | 股东类型（G=高管 P=个人 C=公司） |
| `in_de` | 增减持方向（IN=增持 DE=减持） |
| `change_vol` | 变动股数 |
| `change_ratio` | 占总股本比例 |
| `after_share` | 变动后持股 |
| `after_ratio` | 变动后占比 |
| `avg_price` | 成交均价 |
| `total_share` | 公司总股本 |
| `begin_date` | 变动起始日 |
| `close_date` | 变动截止日 |

## 数据范围

- 起始日期：2019-01-01
- API 路径：`GET /v1/market/holder-trade`
