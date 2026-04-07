# 概念成分

## 背景说明

本接口返回**某个概念板块包含哪些成分股**。关于 A 股概念板块的完整背景说明，请参阅 `concepts` 接口。

### 使用场景
- **找出可交易的成分**：在 `concepts` 中识别出热门题材后，用本接口获取成分股列表做进一步分析。
- **多概念交叉分析**：找出同时属于多个热门概念的股票——板块轮动期常常表现优异。
- **成分变更追踪**：随着相关性变化，概念会增删成分。追踪变更可识别新晋"概念成分"。

### 关键字段解读
- **`ts_code`**：概念指数代码（父级）。
- **`con_code`**：成分股代码（成员）。
- **`name`**：成分股名称（中文）。
- **`trade_date`**：归属记录日期——成分会变化，时间很重要。

### 注意事项
- 同一只股票可同时属于几十个概念。
- 成分由数据商（东方财富）按自有规则决定，不同概念的"纯度"差异很大。

## SDK 方法

```python
client.concept_members(ts_code=None, con_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## 返回类型

`pd.DataFrame` — 无数据时返回空 DataFrame。

## 示例

```python
df = client.concept_members(ts_code="TS2", limit=5)
print(df[["con_code", "name"]])
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
