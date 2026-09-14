# Product Recommendation Workflow

## Trigger Conditions
- User asks for new product direction recommendations
- User says "推荐新品" / "找几个产品方向" / "选品" / "有什么好做的"
- User provides their existing product portfolio and asks for expansion ideas

## Input Requirements
Before generating recommendations, gather:
1. **User's existing product categories** — to avoid recommending overlapping products
2. **Supply chain capabilities** — metalworking, plastics, electronics, textiles, etc.
3. **Preferences** — price range, FBM/FBA, category exclusions, weight limits
4. **Budget** — initial investment range for first batch

If user does not provide these, make reasonable assumptions based on context and state them.

## Output Structure

Generate **3-5 product recommendations** in ranked order (🥇 🥈 🥉 🌟).

### Each Recommendation Must Include:

```
### 🥇 方向一：[产品中文名] / [产品英文名]

**一句话判断：** [一句话总结为什么值得做]

| 关键指标 | 数据 |
|:--------|:----|
| 💰 售价 | $[价格范围] |
| 📦 1688拿货价 | ¥[价格范围] |
| 📊 月销参考 | [头部ASIN月销量] |
| 💵 单件毛利 | $[利润范围] |
| ⚖️ 重量 | [重量范围]，[FBM/FBA友好度] |
| 🏆 竞争判断 | ⭐⭐⭐ [竞争程度描述] |

**为什么适合：**
- ✅ [理由1：市场趋势/需求]
- ✅ [理由2：供应链匹配]
- ✅ [理由3：FBM/物流优势]
- ✅ [理由4：差异化空间]

**切入点建议：** [具体规格建议、定价建议、首批数量]
```

### Comparison Table (Required at End)

```
### 对比总表

| 方向 | 客单价 | 月销潜力 | FBM优势 | 供应链匹配 | 品类全新度 | 首批投入 |
|:----|:-----:|:-------:|:------:|:---------:|:---------:|:-------:|
| 🥇 [产品1] | $[范围] | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ✅ 全新 | ¥[范围] |
| 🥈 [产品2] | ... | ... | ... | ... | ... | ... |
```

### Closing (Required)

End with a proactive follow-up:
```
**Boss，以上推荐您看方向是否合适？需要我调整价格区间、品类偏好，或者针对某个方向做更详细的竞品分析和利润测算吗？😊**
```

## Recommendation Criteria (Blue Ocean + Fast Launch)

Prioritize products that meet ALL of these criteria:

### Must-Have Filters (all must pass)
1. **Monthly sales sweet spot**: Top ASIN monthly sales 100-800 (NOT 1000+). If top ASIN >1000/month, the category is likely too competitive for a new entrant to get quick traction.
2. **Low review barrier**: Top 10 ASINs average <200 reviews. If average >500 reviews, new listings will struggle to rank.
3. **Fast launch signal**: Evidence that new ASINs (30 days old) in this category are already getting orders. Look for ASINs with <50 reviews but appearing in top 20 results.
4. **FBM friendly**: Weight 8-30kg or large volume (FBA fees create natural moat)
5. **1688 sourcable**: Clear supply chain on 1688 with MOQ 50-200 units
6. **Healthy margin**: $30+ net profit per unit, net margin >15%

### Preferred Signals (nice to have)
7. **Low PPC cost**: Estimated CPC < $1.50 (less competition = cheaper ads = faster to first sale)
8. **Brand fragmentation**: No single brand >30% market share (TOP3 click share <25%)
9. **Price range**: $50-200 (broad enough for margin, narrow enough to avoid premium brand wars)
10. **Differentiation potential**: Clear improvement opportunities visible in top competitor差评
11. **Seasonal timing**: Product should NOT be in declining season; ideally entering or in stable season

### Red Flags (auto-reject)
- Top ASIN monthly sales >2000 (red ocean, too competitive)
- Top 10 avg reviews >500 (review barrier too high for new entrant)
- Single brand >40% click share (monopoly, hard to break in)
- ABA search rank <500 (too much search competition)
- Category dominated by Amazon Basics or major brands (Apple, Philips, etc.)

### New ASIN Launch Feasibility Assessment
For each recommendation, assess the likelihood of a new ASIN getting its first order within 30 days:
- **HIGH**: Top 20 has ASINs with <50 reviews, category avg reviews <200, PPC < $1
- **MEDIUM**: Top 20 has some ASINs with <100 reviews, category avg reviews 200-400, PPC $1-2
- **LOW**: All top 20 ASINs have >200 reviews, category avg >400, PPC >$2

## Category Filtering Rules

When user specifies exclusions:
- Parse exclusion keywords (e.g., "不要汽配" = exclude all automotive parts)
- Cross-check each recommendation against exclusion list
- If a recommendation might be borderline, explicitly state why it's included/excluded
- State compliance at the end: "以上推荐全部是非[排除品类]类"

## Blue Ocean Sourcing Strategy

### Search Approach
When searching for blue ocean products, use these search patterns:
- Search Amazon "New Releases" in specific subcategories, not "Best Sellers"
- Look for ASInsight/Jungle Scout data showing categories with low avg reviews
- Search for niche/long-tail keywords with moderate search volume but low competition
- Focus on subcategories, not broad categories (e.g., "heavy duty folding workbench" not "workbench")
- Prioritize products with visible quality gaps in existing listings

### Category Focus Areas (FBM + Blue Ocean)
Based on cross-border e-commerce patterns, these categories tend to have blue ocean pockets:
- **Pet supplies niches**: Pet strollers, pet car seats, cat litter furniture, bird/small animal cages (not dog crates which are red ocean)
- **Outdoor/Garden niches**: Compost tumblers, garden arches, plant stands metal, firewood racks (not deck boxes which are competitive)
- **Garage/Workshop niches**: Folding workbenches, mobile tool carts, pegboard organizers (not standard shelving which is red ocean)
- **Home furniture niches**: Entryway benches with storage, shoe cabinets, wine racks, bar carts (not standard tables)
- **Fitness niches**: Ab rollers with knee pad, adjustable dumbbells small, resistance band sets with door anchor (not treadmills which are red ocean)
- **Auto niches**: Car roof bags, hitch cargo carriers, tailgate tables (not standard auto parts)

### Keyword Discovery Method
1. Start with a broad category (e.g., "outdoor storage")
2. Drill into subcategories (e.g., "outdoor storage cabinet metal lockable")
3. Check if top ASIN monthly sales is 100-800 (sweet spot)
4. Check if top 10 avg reviews <200 (low barrier)
5. Check if any ASIN with <50 reviews appears in top 20 (fast launch signal)
6. Verify 1688 sourcing availability
7. Calculate profit margin

Always tailor recommendations to the user's specific supply chain and preferences.
