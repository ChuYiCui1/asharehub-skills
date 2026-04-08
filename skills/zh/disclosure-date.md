# 财报披露日期

## SDK 方法

```python
client.disclosure_date(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 6 列。无数据时返回空 DataFrame。

## 示例

```python
df = client.disclosure_date(ts_code="000001.SZ", limit=5)
print(df[["end_date", "pre_date", "actual_date"]])
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

ts_code、ann_date(最新公告日)、end_date(报告期)、pre_date(预约披露日)、actual_date(实际披露日)、modify_date(修改日)。

## 数据范围

- 起始日期：2001-02-06
- 用于追踪上市公司财报披露时间
- API 路径：`GET /v1/financials/disclosure-date`
