# 股东户数

## SDK 方法

```python
client.shareholders(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 无数据时返回空 DataFrame。

## 示例

```python
df = client.shareholders(ts_code="000001.SZ", limit=3)
print(df[["end_date", "holder_num"]])
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
| `end_date` | 报告期末 |
| `holder_num` | 股东户数 |

## 数据范围

- 起始日期：2024-01-01
- API 路径：`GET /v1/market/shareholders`

## 备注

- 户数下降通常意味着筹码集中，可作为主力吸筹的参考信号
