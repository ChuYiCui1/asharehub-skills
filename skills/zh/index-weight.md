# 指数权重

## SDK 方法

```python
client.index_weight(index_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.index_weight(index_code="399300.SZ", limit=5)
print(df[["con_code", "con_name", "weight"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `index_code` | str | None | 指数代码，如 `399300.SZ`（沪深300） |
| `start_date` | str | None | 起始日期，YYYY-MM-DD |
| `end_date` | str | None | 结束日期，YYYY-MM-DD |
| `limit` | int | 100 | 返回行数，最大 5000 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 字段 | 说明 |
|------|------|
| `index_code` | 指数代码 |
| `trade_date` | 生效日期 |
| `con_code` | 成分股代码 |
| `con_name` | 成分股名称 |
| `weight` | 权重 % |

## 常用指数

| 代码 | 名称 |
|------|------|
| `399300.SZ` | 沪深300 |
| `000905.SH` | 中证500 |
| `000016.SH` | 上证50 |

## 备注

- API 路径：`GET /v1/indices/index-weight`
