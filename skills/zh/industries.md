# 行业分类

## SDK 方法

```python
client.industry_list(ts_code=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 无数据时返回空 DataFrame。

## 示例

```python
df = client.industry_list(ts_code="000001.SZ")
print(df[["ts_code", "l1_name", "l2_name", "l3_name"]])
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
| `name` | 股票名称 |
| `l1_code` | 一级行业代码 |
| `l1_name` | 一级行业名称（共 31 个） |
| `l2_code` | 二级行业代码 |
| `l2_name` | 二级行业名称 |
| `l3_code` | 三级行业代码 |
| `l3_name` | 三级行业名称 |

## 数据范围

- 数据类型：静态数据
- 分类标准：申万 2021（SW2021）
- API 路径：`GET /v1/reference/industries`
