# 龙虎榜

## SDK 方法

```python
client.top_list(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
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
| `trade_date` | 交易日期 |
| `ts_code` | 股票代码 |
| `name` | 股票名称 |
| `close` | 收盘价 |
| `pct_change` | 涨跌幅 % |
| `turnover_rate` | 换手率 % |
| `amount` | 成交额 |
| `l_sell` | 机构卖出额 |
| `l_buy` | 机构买入额 |
| `l_amount` | 机构成交总额 |

## 数据范围

- 起始日期：2024-01-02
- 记录数：3.5万+
- API 路径：`GET /v1/market/top-list`
