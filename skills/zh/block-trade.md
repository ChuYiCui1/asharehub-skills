# 大宗交易

## SDK 方法

```python
client.block_trade(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
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
| `trade_date` | 交易日期 |
| `price` | 成交价 |
| `vol` | 成交量（万股） |
| `amount` | 成交额（万元） |
| `buyer` | 买方营业部 |
| `seller` | 卖方营业部 |

## 数据范围

- 起始日期：2010-01-04
- 记录数：16.9万+
- API 路径：`GET /v1/market/block-trade`
