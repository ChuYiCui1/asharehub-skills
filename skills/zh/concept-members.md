# 概念成分

## SDK 方法

```python
client.concept_members(ts_code=None, con_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 板块代码，如 `BK0425.DC` |
| `con_code` | str | None | 成分股代码，如 `000001.SZ` |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `trade_date` | 交易日期 |
| `ts_code` | 板块代码 |
| `con_code` | 成分股代码 |
| `name` | 股票名称 |

## 数据范围

- 起始日期：2025-01-02
- 记录数：67.8万+
- API 路径：`GET /v1/market/concept-members`
