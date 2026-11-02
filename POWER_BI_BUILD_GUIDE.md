# Power BI Desktop build guide — TR-102 Cosmetics Analytics

## Import
1. Open Power BI Desktop → **Get data → Text/CSV**.
2. Import `Products_Clean.csv` first. In Power Query, confirm `Price`, `Rank`, `IngredientCount`, and skin flags are numeric.
3. Import `Category_Summary.csv`, `Brand_Summary.csv`, `SkinType_Summary.csv`, and `Ingredient_Frequency.csv` for supporting visuals.
4. Use **Close & Apply**. Save as `TR102_Cosmetics_Analytics.pbix`.

## Starter DAX measures
```DAX
Product Count = COUNTROWS(Products_Clean)
Average Listed Price = AVERAGE(Products_Clean[Price])
Median Listed Price = MEDIAN(Products_Clean[Price])
Average Rank = AVERAGE(Products_Clean[Rank])
Average Ingredient Count = AVERAGE(Products_Clean[IngredientCount])
Brand Count = DISTINCTCOUNT(Products_Clean[Brand])
```

## Recommended report layout
- KPI cards: Product Count, Average Listed Price, Average Rank, Average Ingredient Count.
- Clustered bar chart: `Label` by count of `Name`.
- Column chart: `Label` by average `Price`.
- Bar chart: skin type vs number of products flagged; use the supplied `SkinType_Summary` table or unpivot the five flag columns in Power Query.
- Histogram-style column chart: `Price` bins by product count.
- Scatter chart: `Price` vs `Rank`, details `Name`, legend `Label`.
- Table: `Name`, `Brand`, `Label`, `Price`, `Rank`, `IngredientCount`.
- Slicers: `Label`, `Brand`, and one skin-type field or a normalized skin-type table.

## Validation before submission
- Compare the product count card with the source CSV row count (1,472).
- Verify average price/rank against the notebook summary.
- Test each slicer and confirm visuals respond as expected.
- Add a note: **Price currency is not specified in the source data.**
- Add a note: ingredient-list similarity and source skin-type flags are not medical advice.
- Save the `.pbix` file and export a PDF or screenshots if required by your department.

**Important:** The local HTML dashboard is a preview/prototype. It is not a Power BI `.pbix` file. The `.pbix` must be created and saved in Power BI Desktop.
