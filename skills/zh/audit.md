# 审计意见 — 年报审计结果

## SDK 方法

```python
client.audit(ts_code=None, start_date=None, end_date=None, limit=50, offset=0)
```

## 返回类型

`pd.DataFrame` — 7 列。无数据时返回空 DataFrame。

## 示例

```python
df = client.audit(ts_code="000001.SZ", limit=3)
print(df[["end_date", "audit_result", "audit_agency", "audit_fees"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 起始日期 YYYY-MM-DD |
| `end_date` | str | None | 结束日期 YYYY-MM-DD |
| `limit` | int | 50 | 返回行数，最大 1000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

ts_code、ann_date、end_date、audit_result(审计意见类型)、audit_fees(审计费用)、audit_agency(审计机构)、audit_sign(签字会计师)。

## 数据范围

- 起始日期：2006-04-20
- 仅年度数据（年报披露时发布）
- API 路径：`GET /v1/financials/audit`
