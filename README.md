# State Minimum Wage Rates 2027 and Related Measures (startbusinessbystate.com)

State minimum wages now and on January 1, 2027, with rent, pay, cost, border and price-adjusted comparisons for all 50 states and DC.

Main page: https://startbusinessbystate.com/minimum-wage-by-state-2027/

## Summary

This dataset tracks the minimum wage in every state and DC today (October 2026) and on January 1, 2027. It also compares those rates with rent, with what workers in low-wage jobs actually earn, with the extra payroll cost for a small employer, with neighboring states, and with local prices. It backs a six-page series on startbusinessbystate.com.

## Files

| File | Rows | What it is |
|---|---|---|
| `data/minimum_wage_2027_raise_cost.csv` | 15 | Extra wage cost of the next scheduled raise for a small employer, in states with a raise. |
| `data/minimum_wage_2027_vs_wages_by_occupation.csv` | 225 | For 15 states with a rate change or a $15 floor, how the rate compares with actual pay in 14 low-wage jobs plus all jobs. |
| `data/minimum_wage_border_gaps_2027.csv` | 23 | Neighboring state pairs with the biggest legal minimum wage gap in 2027, and the gap in actual pay. |
| `data/minimum_wage_by_state_2027.csv` | 51 | One row per state: the rate today, the January 1, 2027 rate and its status. |
| `data/minimum_wage_vs_rent_by_state.csv` | 51 | Hours of minimum-wage work needed to afford a one-bedroom Fair Market Rent. |
| `data/real_minimum_wage_by_state.csv` | 51 | Minimum wages adjusted for local prices, and hours of work for an average home electric bill. |

All files are UTF-8 CSV with a header row in snake_case. Blank cells mean the value is not available, not applicable, or suppressed by the source.

## Data dictionary

### data/minimum_wage_2027_raise_cost.csv

Extra wage cost of the next scheduled raise for a small employer, in states with a raise. Rows: 15. Columns: 13.

| Column | Meaning | Units |
|---|---|---|
| `state` | State name (50 states plus District of Columbia). | text |
| `abbr` | Two-letter USPS state code. | text |
| `minimum_wage_before` | Rate before the change. | US dollars per hour |
| `minimum_wage_after` | Rate after the change. | US dollars per hour |
| `effective_date` | Date the new rate starts. | date (YYYY-MM-DD) |
| `rate_status` | set, expected, pending or already in effect. | category |
| `raise_per_hour` | minimum_wage_after minus minimum_wage_before. | US dollars per hour |
| `raise_pct` | Raise as a percent of the old rate. | percent |
| `extra_wages_per_full_time_worker_per_year` | raise_per_hour x 2,080. | US dollars per year |
| `extra_wages_10_full_time_workers` | Ten full-time workers at the minimum. | US dollars per year |
| `extra_cost_10_workers_with_employer_fica` | Ten workers plus the 7.65% employer FICA share. | US dollars per year |
| `restaurant_locations_2023` | Restaurant and bar establishments (NAICS 722), Census County Business Patterns 2023. | establishments |
| `restaurant_locations_under_20_employees` | Of those, establishments with fewer than 20 employees. | establishments |

### data/minimum_wage_2027_vs_wages_by_occupation.csv

For 15 states with a rate change or a $15 floor, how the rate compares with actual pay in 14 low-wage jobs plus all jobs. Rows: 225. Columns: 14.

| Column | Meaning | Units |
|---|---|---|
| `state` | State name (50 states plus District of Columbia). | text |
| `abbr` | Two-letter USPS state code. | text |
| `occupation` | Occupation title (shortened BLS SOC title). | text |
| `soc_code` | BLS Standard Occupational Classification code (00-0000 = all occupations). | code |
| `jobs_may_2025` | Employment in the occupation in the state, May 2025 (blank if suppressed). | jobs |
| `p10` | 10th percentile hourly wage, May 2025. | US dollars per hour |
| `p25` | 25th percentile hourly wage, May 2025. | US dollars per hour |
| `median` | Median (50th percentile) hourly wage, May 2025. | US dollars per hour |
| `p75` | 75th percentile hourly wage, May 2025. | US dollars per hour |
| `minimum_wage_compared` | The minimum wage used for the comparison. | US dollars per hour |
| `rate_basis` | Which rate is compared: the January 1, 2027 rate or the current rate where no 2027 change applies. | category |
| `rate_status` | set, expected or pending (see minimum_wage_by_state_2027.csv). | category |
| `where_rate_falls` | Where the rate falls in the pay range: below 10th percentile, at or above 10th, 25th or median, or wage data suppressed. | category |
| `est_share_of_jobs_paid_less_pct` | Estimated share of jobs in the occupation paid less than the rate, by straight-line interpolation between percentiles. "<10" means below the 10th percentile. | percent |

### data/minimum_wage_border_gaps_2027.csv

Neighboring state pairs with the biggest legal minimum wage gap in 2027, and the gap in actual pay. Rows: 23. Columns: 13.

| Column | Meaning | Units |
|---|---|---|
| `higher_minimum_state` | State with the higher 2027 minimum. | text |
| `lower_minimum_state` | Neighboring state with the lower minimum. | text |
| `min_wage_higher_jan_2027` | January 1, 2027 minimum in the higher state. | US dollars per hour |
| `min_wage_lower_jan_2027` | January 1, 2027 minimum in the lower state. | US dollars per hour |
| `legal_gap_per_hour` | Difference in minimum wages. | US dollars per hour |
| `legal_gap_full_time_per_year` | legal_gap_per_hour x 2,080. | US dollars per year |
| `fast_food_median_higher_may_2025` | Median wage of fast food and counter workers (SOC 35-3023), higher state, May 2025. | US dollars per hour |
| `fast_food_median_lower_may_2025` | Same, lower state. | US dollars per hour |
| `fast_food_median_gap` | Difference in those medians. | US dollars per hour |
| `cashier_median_higher_may_2025` | Median wage of cashiers (SOC 41-2011), higher state, May 2025. | US dollars per hour |
| `cashier_median_lower_may_2025` | Same, lower state. | US dollars per hour |
| `cashier_median_gap` | Difference in those medians. | US dollars per hour |
| `notes` | Notes, for example when a rate is pending or expected. | text |

### data/minimum_wage_by_state_2027.csv

One row per state: the rate today, the January 1, 2027 rate and its status. Rows: 51. Columns: 10.

| Column | Meaning | Units |
|---|---|---|
| `state` | State name (50 states plus District of Columbia). | text |
| `abbr` | Two-letter USPS state code. | text |
| `minimum_wage_oct_2026` | State minimum wage in effect in October 2026 (federal $7.25 where no higher state rate applies). | US dollars per hour |
| `minimum_wage_jan_1_2027` | Rate in effect on January 1, 2027. "pending" means the state indexes its rate and has not announced it yet. If a state changes on another date, this column holds the rate on January 1, 2027 and the notes column gives the later change. | US dollars per hour, or the text pending |
| `change_dollars` | minimum_wage_jan_1_2027 minus minimum_wage_oct_2026. | US dollars per hour |
| `change_pct` | Change as a percent of the October 2026 rate. | percent |
| `status` | How the January 1, 2027 figure is known: Announced by the state, Set in state law, Expected (press reports), Pending (not announced yet), Changes later, No change scheduled, or Federal $7.25. | category |
| `extra_pay_per_full_time_worker_per_year` | change_dollars x 2,080 hours. | US dollars per year |
| `notes` | Plain-language notes (later changes, regional rates, caveats). | text |
| `source` | Source for the 2027 figure. | text |

### data/minimum_wage_vs_rent_by_state.csv

Hours of minimum-wage work needed to afford a one-bedroom Fair Market Rent. Rows: 51. Columns: 12.

| Column | Meaning | Units |
|---|---|---|
| `state` | State name (50 states plus District of Columbia). | text |
| `abbr` | Two-letter USPS state code. | text |
| `fair_market_rent_1br_fy2027` | Population-weighted fiscal 2027 HUD Fair Market Rent for a one-bedroom unit. | US dollars per month |
| `fair_market_rent_1br_fy2026` | Same measure for fiscal 2026. | US dollars per month |
| `rent_change_pct` | Change from fiscal 2026 to fiscal 2027. | percent |
| `minimum_wage_oct_2026` | Minimum wage in effect in October 2026. | US dollars per hour |
| `hours_per_week_needed_now` | Weekly hours at today's minimum wage needed to keep one-bedroom rent at 30% of pay (rent x 12 / 0.30 / 52 / wage). | hours per week |
| `hours_of_work_to_pay_one_month_rent` | Hours at today's minimum wage equal to one month of one-bedroom rent (rent / wage). | hours |
| `minimum_wage_jan_1_2027` | Minimum wage on January 1, 2027 (blank if pending). | US dollars per hour |
| `hours_per_week_needed_jan_2027` | Same as hours_per_week_needed_now at the January 1, 2027 rate. | hours per week |
| `rate_status` | blank = rate set; expected = based on press reports; pending = not announced or calculated from a percent in law. | category |
| `housing_wage_1br_40hrs` | Hourly pay a 40-hour worker needs to keep one-bedroom rent at 30% of pay (rent x 12 / 0.30 / 2,080). | US dollars per hour |

### data/real_minimum_wage_by_state.csv

Minimum wages adjusted for local prices, and hours of work for an average home electric bill. Rows: 51. Columns: 12.

| Column | Meaning | Units |
|---|---|---|
| `state` | State name (50 states plus District of Columbia). | text |
| `abbr` | Two-letter USPS state code. | text |
| `regional_price_parity_2024` | BEA Regional Price Parity, all items, 2024 (U.S. = 100). | index |
| `minimum_wage_oct_2026` | Minimum wage in effect in October 2026. | US dollars per hour |
| `real_minimum_wage_now` | minimum_wage_oct_2026 x 100 / regional_price_parity_2024. | US dollars per hour at national average prices |
| `rank_now` | Rank of real_minimum_wage_now (1 = highest). | rank |
| `minimum_wage_jan_1_2027` | Rate on January 1, 2027, or "pending". Rates calculated from a percent in law keep 4 decimals. | US dollars per hour |
| `real_minimum_wage_jan_2027` | Price-adjusted January 1, 2027 rate. | US dollars per hour at national average prices |
| `rank_jan_2027` | Rank of real_minimum_wage_jan_2027 (1 = highest). | rank |
| `rate_status_2027` | set, expected or pending. | category |
| `avg_residential_electric_bill_monthly` | Residential electricity revenue / customers / 12, August 2025 to July 2026 (EIA). | US dollars per month |
| `hours_of_minimum_wage_work_for_electric_bill` | avg_residential_electric_bill_monthly / minimum_wage_oct_2026. | hours |

## Sources

| Source | Link | License or status |
|---|---|---|
| U.S. Department of Labor, Wage and Hour Division, state minimum wage table (updated July 1, 2026) | https://www.dol.gov/agencies/whd/minimum-wage/state | Public domain (U.S. government work) |
| State labor agency notices and state statutes for 2027 rates (for example the Nebraska DOL schedule updated July 31, 2026 and the California Department of Finance certification of July 31, 2026). The source for each state is in the source column. | https://www.dol.gov/agencies/whd/state/contacts | Facts from government sources |
| HUD Fair Market Rents, fiscal 2027 and 2026 | https://www.huduser.gov/portal/datasets/fmr.html | Public domain (U.S. government work) |
| BLS Occupational Employment and Wage Statistics (OEWS), May 2025 state estimates | https://www.bls.gov/oes/ | Public domain (U.S. government work) |
| Census County Business Patterns 2023, NAICS 722 (restaurants) | https://www.census.gov/programs-surveys/cbp.html | Public domain (U.S. government work) |
| BEA Regional Price Parities by state, 2024 | https://www.bea.gov/data/prices-inflation/regional-price-parities-state-and-metro-area | Public domain (U.S. government work) |
| EIA retail electricity sales, residential revenue and customers, August 2025 to July 2026 | https://www.eia.gov/electricity/data.php | Public domain (U.S. government work) |
| Census population estimates (used to population-weight county rents) | https://www.census.gov/programs-surveys/popest.html | Public domain (U.S. government work) |

## Methodology

- Current rates come from the DOL state table (updated July 1, 2026). Florida uses its September 30, 2026 step from FloridaCommerce.
- January 1, 2027 rates come from the state agency notice where one has been published, or from the state law when the law fixes the amount. Each row says which (status column). Where a state indexes its rate to inflation and has not announced the 2027 figure yet, the 2027 cell says pending.
- Arizona's $15.65 is marked Expected because, as of this release, it rests on news reports of the Industrial Commission announcement. We could not read the agency notice itself.
- Where no state law exists or the state rate is below $7.25, the federal $7.25 is used.
- Full-time year = 2,080 hours (40 hours x 52 weeks).
- Rent: the fiscal 2027 one-bedroom Fair Market Rent for each county, weighted by county population to get one state figure. Hours per week needed = hours of work that keep rent at 30% of pay. Housing wage = hourly pay a 40-hour worker needs to keep the one-bedroom rent at 30% of pay.
- Pay comparison: each state's rate is compared with the 10th, 25th and 50th percentile hourly pay for 14 common low-wage jobs (BLS OEWS, May 2025). The estimated share paid less is a straight-line estimate between published percentiles, so treat it as approximate.
- Raise cost: extra yearly wages = raise per hour x 2,080 hours. The 10-worker figure with FICA adds the 7.65% employer share of Social Security and Medicare.
- Real minimum wage = rate x 100 / BEA Regional Price Parity (U.S. = 100).
- Average home electric bill = residential revenue / residential customers / 12, August 2025 to July 2026.

## Limitations

- Rates change. Five states (Montana, South Dakota, Vermont, New York and Arizona's official notice) were still pending or unconfirmed on October 2, 2026. Check the state agency before relying on a 2027 figure.
- The tables show the standard adult rate only. Tipped, youth, training, small-employer and local (city or county) rates are not included. New York's upstate rate is noted in the notes column.
- OEWS pay is from May 2025 and has gone up since. Percentile interpolation is an estimate.
- Fair Market Rents are a HUD program measure (around the 40th percentile of rents), not the average rent.
- Regional Price Parities are for 2024, the latest available.

## As-of date

October 2, 2026 (rates checked through this date; Nebraska 2027 rate confirmed October 2, 2026)

Version 1.0.0, released 2026-10-02.

## How to cite

StartBusinessByState. (2026). *State Minimum Wage Rates 2027 and Related Measures (startbusinessbystate.com)* (Version 1.0.0) [Data set]. startbusinessbystate.com. https://github.com/jameyriley46-ux/startbusinessbystate-minimum-wage-2027

Please also credit the original sources listed above. When you use the data, a link back to https://startbusinessbystate.com/minimum-wage-by-state-2027/ is appreciated.

## Related pages on startbusinessbystate.com

- https://startbusinessbystate.com/minimum-wage-by-state-2027/
- https://startbusinessbystate.com/minimum-wage-vs-rent-by-state/
- https://startbusinessbystate.com/minimum-wage-2027-vs-what-workers-earn/
- https://startbusinessbystate.com/minimum-wage-increase-cost-small-business-2027/
- https://startbusinessbystate.com/minimum-wage-border-states-2027/
- https://startbusinessbystate.com/real-minimum-wage-by-state/

## License

This dataset is released under the Creative Commons Attribution 4.0 International license (CC BY 4.0). See `LICENSE`. You may share and adapt it, including for commercial use, as long as you give credit.
Underlying public domain data from U.S. government agencies stays public domain. Data from CC BY sources (such as LegiScan, PatentsView, Epoch AI or the Anthropic Economic Index, where used) also requires credit to those sources.

## Contact

StartBusinessByState (startbusinessbystate.com) (https://startbusinessbystate.com/)
