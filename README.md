# Personality Report - Power BI Project

## Project Overview
This Power BI project analyzes survey data from **YouGov.com**, where men and women across 20 countries shared what matters most when choosing their soulmate.  
The report highlights priority rankings (1st to 6th) of different attributes such as looks, intelligence, wealth, sense of humor, similar interests, and personality.  

The dashboard enables comparisons by **country, gender, and attribute preference**, giving insights into cultural and gender-based differences in partner expectations.

---

## Data Source
**Excel File:** `Looks vs Personality.xlsx`  
**Columns in raw dataset:**
- Unweighted Sample  
- Weighted Sample  
- Question  
- Nationality  
- Gender  
- Rank Text  
- Rank Number  
- Percentage  

**Total Records:** 1,440  

---

## Data Transformation (Power Query & DAX)

## 1. Conditional Column: `Attributes`
Since the `Question` column had long text values, a new column `Attributes` was created:  

```DAX
Attributes = 
SWITCH(
    TRUE(),
    [Question] = "They are good looking", "Looks",
    [Question] = "They have a personality I like", "Personality",
    [Question] = "They have a sense of humour I like", "Sense of Humour",
    [Question] = "They are intelligent", "Intelligent",
    [Question] = "They make decent money", "Wealthy",
    [Question] = "They have similar interests to me", "Similar Interest"
)
```

## 2. Rank Text Transformation
- Split **Rank Text** column by delimiter `"space"` to isolate ranking words (First, Second, … Sixth)  
- Transformed the new column to **Capitalize Each Word** (First, Second, etc.)  
- Deleted the original Rank Text column and replaced it with the cleaned version  

## 3. Final Columns after Transformation
- Attributes  
- Gender  
- Nationality  
- Percentage  
- Question  
- Rank Number  
- Rank Text  
- Unweighted Sample  
- Weighted Sample  

---

## Dashboard Design

### Layout
Applied imported **theme** and **custom background**.  
Layout divided into three sections:
1. **Left section** → Slicers  
2. **Upper section** → Report Title & Filters  
3. **Main section** → Charts and Analysis  

### Features
- **Title**: *Personality Survey*  
- **Slicers**:
  - Vertical slicer → **Nationality** (labelled *“Choose Country”*)  
  - Horizontal slicer → **Ranked** (sorted using Rank Number for chronological order)  
- **Charts**:
  - Donut Chart 1 → *Percentage vs Attributes (Male only)*  
  - Donut Chart 2 → *Percentage vs Attributes (Female only)*  
  - Gender logos (man/woman) added inside donut chart holes  
- **Separators**: Lines used to distinguish slicers, charts, and headers  

---

## Important Modelling Step
To display ranking order correctly:
1. Highlight **Rank Text** column in the Fields pane  
2. Go to **Modeling → Sort by Column**  
3. Choose **Rank Number**  

This ensures the slicer shows *First → Sixth* in the correct order  

---

## Key Insights
- Attribute preferences ranked by **men vs women** across countries  
- Top priorities for finding a soulmate vary by **culture and nationality**  
- Visualization of how attributes shift in importance based on **gender**  

---

## Tools Used
- **Power BI Desktop** → Data modeling, transformation, visualization  
- **Excel** → Raw data source  

---

## Author
**Debashis**
![Capture](https://github.com/user-attachments/assets/0030823d-7a58-40fc-b281-4c0956206751)

