# Exploratory Data Analysis (EDA) – World Layoffs (SQL / MySQL)

I used SQL in MySQL Workbench to explore the World Layoffs dataset after cleaning it.  
All queries run against my cleaned table: `layoffs_staging2`.

This repo is focused on answering practical questions like: “Where were layoffs highest?”, “Which industries were hit hardest?”, and “How did layoffs change over time?”

## What I looked at
Here’s what I explored using SQL:

- Quick scan of the table to understand the columns and values
- Biggest single layoff events (max `total_laid_off`) and highest layoff percentages
- Companies that laid off **100%** of staff (and how much funding they raised)
- Total layoffs by **country**, **industry**, and **funding stage**
- Date range of the dataset (min/max date)
- Layoffs over time:
  - totals by **year**
  - totals by **month**
  - a **rolling cumulative total** using a window function
- Company impact:
  - total layoffs by company & year
  - **Top 5 companies each year** by layoffs using `DENSE_RANK()`

## Files
- `layoffs_eda.sql` – all the SQL queries used in this analysis (with section comments)

## How to run it
1. Open MySQL Workbench
2. Make sure your cleaned table is available as `layoffs_staging2`
3. Run the queries in `layoffs_eda.sql` section-by-section

## Notes / small assumptions
- Monthly trend uses `SUBSTRING(date, 1, 7)` to group by `YYYY-MM`
- The “top 5 per year” logic uses `DENSE_RANK()` partitioned by year

## If I extend this next
- Build a simple Power BI / Tableau dashboard for the monthly trend + top countries/industries
- Add a few “business-style” questions (e.g., top industries by year, country-by-year heatmap)
