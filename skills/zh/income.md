# 利润表

## SDK 方法

```python
client.income(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.income(ts_code="000001.SZ", limit=3)
print(df[["end_date", "revenue", "n_income"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 报告期起始，YYYY-MM-DD |
| `end_date` | str | None | 报告期截止，YYYY-MM-DD |
| `limit` | int | 20 | 返回行数，最大 200 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 分类 | 字段 |
|------|------|
| **营收** | `total_revenue`, `revenue` |
| **成本** | `total_cogs`, `oper_cost`, `sell_exp`, `admin_exp`, `fin_exp`, `rd_exp` |
| **利润** | `operate_profit`, `total_profit`, `n_income`, `n_income_attr_p` |
| **每股** | `basic_eps`, `diluted_eps` |
| **其他** | `ebit`, `ebitda`, `income_tax` |

## 备注

- 金额单位：元（CNY）
- `end_date` 为报告期（如 2024-12-31 为年报，2024-06-30 为半年报）
- API 路径：`GET /v1/financials/income`
