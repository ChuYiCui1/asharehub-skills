# 概念板块

## SDK 方法

```python
client.concepts(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 板块代码，如 `BK0425.DC` |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 板块代码（如 BK0425.DC） |
| `trade_date` | 交易日期 |
| `name` | 板块名称 |
| `leading` | 领涨股 |
| `leading_code` | 领涨股代码 |
| `pct_change` | 涨跌幅 % |
| `leading_pct` | 领涨股涨幅 |
| `total_mv` | 总市值（万元） |
| `turnover_rate` | 换手率 % |
| `up_num` | 上涨家数 |
| `down_num` | 下跌家数 |
| `idx_type` | 指数类型 |
| `level` | 级别 |

## 数据范围

- 起始日期：2025-01-02
- 记录数：10.9万+
- 概念数量：508 个
- API 路径：`GET /v1/market/concepts`
