# Hospital Dashboard Analysis (2019)

An Excel-based analytics dashboard and written report on **403 hospital visits** recorded between **January 1 and December 20, 2019**. The project explores visit volume, patient risk category, and outcomes (survived or died) to surface mortality trends and data-quality issues.

## Key Findings

| Metric | Value |
|---|---|
| Total visits | **403** |
| Deaths | **69** (17.1% mortality rate) |
| High-risk visits | 182 (45.2%) |
| Mortality, High risk | **21.4%** (39 of 182) |
| Mortality, Low risk | **13.6%** (30 of 221) |

- **January had the highest volume** (62 visits). From March to November, volume settled at roughly 30 to 31 visits per month.
- **August had the highest monthly mortality rate:** 29.0% (9 deaths out of 31 visits).
- **High-risk patients show a higher mortality rate** (about 1.6x), but the difference is borderline statistically (chi-square test, p ≈ 0.051), so it is an association, not proof.
- **Quarterly mortality:** Q1 16.5%, Q2 17.6%, Q3 20.7%, Q4 13.6% (December is incomplete).

## Dataset

The raw data lives in `Sheet1` of the workbook, with 5 columns:

| Column | Description |
|---|---|
| `Visit ID` | Unique visit identifier (range 120 to 8999, with gaps) |
| `Check in Date` | Date of check-in |
| `Risk Category` | `High` or `Low` |
| `Outcome` | `Live` or `Die` |
| `Month` | Month label in `YYYY-MM` format |

Data quality: no missing values, no duplicate visit IDs.

## Workbook Structure

`Hospital_Dashboard.xlsx` contains three sheets:

1. **Sheet1**: the raw visit-level data.
2. **Pivot Tables**: seven pivots (monthly visits, risk distribution, outcome distribution, monthly deaths, monthly mortality rate, deaths by risk category, monthly visits by risk category).
3. **Dashboard**: five charts (monthly deaths trend, risk distribution, outcome distribution, monthly visits by risk, deaths by risk) with an interactive slicer.

## Repository Layout

```
.
├── Hospital_Dashboard.xlsx          # Data, pivot tables, and dashboard
├── Hospital_Dashboard_Report.pdf    # Written analysis report (3 pages)
└── README.md
```

## Limitations

- **December is incomplete** (data ends on December 20), so comparing it with other months is not like-for-like.
- **Small monthly samples** (20 to 62 visits): a single death shifts a monthly rate by about 3 points, so quarterly or annual rates are more reliable.
- **Likely a sample:** the gaps in Visit IDs suggest the file does not cover every hospital visit.
- **Limited variables:** with only risk category and outcome, the data cannot explain *why* mortality differs. Age, department, and diagnosis would help.

## Recommendations

1. Collect richer data (age, department, diagnosis, length of stay).
2. Review the August cases for operational or seasonal causes.
3. Report mortality quarterly instead of monthly, ideally with confidence intervals.
4. Complete the December data before publishing any annual figures.

## Tools

- Microsoft Excel (pivot tables, charts, slicers)
- Python (pandas, SciPy, Matplotlib) for verification and statistical testing
- PDF report generated from HTML with WeasyPrint

## License

Released for educational and portfolio purposes. The dataset is used as provided and contains no personal identifiers.
