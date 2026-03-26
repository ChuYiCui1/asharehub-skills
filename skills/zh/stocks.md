# 股票列表

## SDK 方法

```python
client.stock_list(ts_code=None, limit=100, offset=0)
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码，如 `000001.SZ`（平安银行）、`600519.SH`（贵州茅台） |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `ts_code` | 股票代码 |
| `symbol` | 证券代码 |
| `name` | 股票名称 |
| `area` | 地域 |
| `industry` | 行业 |
| `fullname` | 公司全称 |
| `enname` | 英文名 |
| `cnspell` | 拼音缩写 |
| `market` | 市场 |
| `exchange` | 交易所 |
| `curr_type` | 币种 |
| `list_status` | 上市状态（L=上市 D=退市 P=暂停） |
| `list_date` | 上市日期 |
| `delist_date` | 退市日期 |
| `is_hs` | 沪深港通标的（H/S/N） |

## 数据范围

- 数据类型：静态数据
- 记录数：5,491 只
- API 路径：`GET /v1/reference/stocks`
