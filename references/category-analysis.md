# Category Analysis Workflow

## Trigger Conditions
- User asks "XX品类能不能做" / "分析一下XX" / "看看XX市场"
- User wants to evaluate a specific product category for Amazon US market
- User asks about viability of a specific product type

## Input Requirements
Gather from user:
1. **Target category** — specific product type to analyze
2. **Fulfillment model** — FBM or FBA (default: FBM for large items)
3. **Sourcing channel** — 1688 or other (default: 1688)
4. **Specific concerns** — price competition, weight/shipping, quality, etc.

## Output Structure

### 1. Category Overview

```
### 品类概况

**一句话判断：** ✅/❌ [可以/不可以做，但需选对细分赛道]

| 维度 | 数据 |
|:----|:------|
| 💰 主流售价 | $[价格范围]（按规格分档列出） |
| 📊 市场规模 | $[市场规模]（[年份]），预计[年份]$[预测规模]，CAGR [增长率] |
| 🏆 头部竞品 | [品牌1] $[价格] / [品牌2] $[价格] / [品牌3] $[价格] |
| 📦 月销参考 | TOP ASIN [月销范围] |
| 📱 1688拿货 | ¥[价格范围]（按规格分档） |
| ⚖️ 重量 | [重量范围]（按规格分档） |
```

### 2. Competitor Analysis (TOP 5)

```
### 竞品分析（TOP 5）

| 品牌 | 规格 | 售价 | 评分 | 月销 | 绳类型/关键属性 | 核心卖点 |
|:----|:---:|:---:|:---:|:---:|:-----:|:--------|
| **[Brand 1]** | [spec] | $[price] | [rating]★ | [sales] | [attribute] | [key selling point] |
| **[Brand 2]** | ... | ... | ... | ... | ... | ... |
```

Include columns relevant to the specific category (e.g., rope type for winches, material for crates).

### 3. Profit Calculation

Provide profit calculations for **at least 2 specifications/configurations** — typically a low-end and high-end option.

```
### 利润测算（[规格描述]，FBM模式）

| 成本项 | 金额 | 说明 |
|:------|:---:|:----|
| ① 1688拿货价 | ¥[price] | [规格描述] |
| ② 国内运到港口 | ¥[price] | |
| ③ 海运头程（美西） | ¥[price] | 体积约[CBM]，重量[kg]，拼箱 |
| ④ 关税 | ¥[price] | 25% |
| ⑤ 海外仓操作费 | ¥[price] | 卸货上架 |
| ⑥ FBM尾程运费 | $[price] | 约¥[CNY]，[重量] |
| ⑦ 亚马逊佣金 | 15% | $[amount] |
| ⑧ 广告费 | 10% | $[amount] |

**利润核算（售价$[price]）：**

| 项目 | 金额 |
|:----|:---:|
| 💰 售价 | $[price] |
| 佣金（15%） | -$[amount] |
| 广告费（10%） | -$[amount] |
| 产品成本 | -¥[CNY] ≈ -$[USD] |
| 头程+关税 | -¥[CNY] ≈ -$[USD] |
| 海外仓操作 | -¥[CNY] ≈ -$[USD] |
| FBM尾程 | -$[amount] |
| **单台净利润** | **≈ $[amount]** |
| **净利率** | **≈ [percentage]%** |
```

### 4. Decision Summary

```
### 判断结论

| 细分方向 | 可行性 | 结论 |
|:--------|:-----:|:-----|
| **[规格1]**（[key params]） | ✅ **可以做** | [净利率]，[reasoning] |
| **[规格2]**（[key params]） | ❌ **不建议** | [reasoning] |
| **[规格3]**（[key params]） | ❌ **不建议** | [reasoning] |

**核心结论：** [2-3句话总结判断，指出唯一可行的细分方向及原因]

**切入点建议：** [具体规格、定价、首批数量建议]
```

### 5. Closing

End with proactive follow-up:
```
**Boss，这个分析您觉得如何？需要我针对[相关方向]做更详细的分析吗？😊**
```

## Analysis Methodology

### Market Data Collection
1. **Search Amazon.com** for the category — note top 10 results
2. **Extract data points**: price, rating, review count, BSR rank, estimated monthly sales
3. **Search market reports** — look for industry market size, growth rate (CAGR)
4. **Search 1688.com** — get wholesale prices for different specifications
5. **Calculate shipping** — estimate CBM and weight for freight calculation

### Competitor Evaluation Criteria
- **Price positioning**: Where do competitors cluster?
- **Review quality**: What are common complaints? (differentiation opportunities)
- **Sales volume**: Is there enough demand?
- **Brand concentration**: Is the market dominated by one brand or fragmented?
- **Chinese seller presence**: Have Chinese brands already succeeded? (validates feasibility)

### Go/No-Go Decision Framework
- **GO** if: net margin > 8%, monthly sales potential > 200 units, clear differentiation path
- **CONDITIONAL GO** if: net margin 3-8% but high volume potential or strategic value
- **NO-GO** if: net margin < 3%, market dominated by entrenched brands, no differentiation possible

Always provide the decision in a clear table format with explicit ✅/❌ markers.
