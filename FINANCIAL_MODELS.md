# Financial Models and Formulas for Profit Per Job Calculator

This document outlines the detailed financial models and formulas used in the "Profit Per Job Calculator" Excel application. These models are designed to provide business owners in the residential cleaning space with insights into job profitability, cost management, and pricing strategies.

## Detailed Financial Models and Formulas

### 1. Dashboard Summary
Provides an overview of key metrics based on data from other sheets.
*   **Average Profit per Job:** `='Job Costing'!B21`
*   **Total Monthly Profit (Est):** `=(B3*B2)-'Overhead & Break-Even'!B8`
*   **Break-Even Number of Jobs:** `='Overhead & Break-Even'!B10`

### 2. Job Costing
Calculates the direct costs and profitability of an individual job.
*   **Inputs:** Total Job Price (Revenue), Estimated Labor Hours, Hourly Labor Rate, Other Direct Costs, Estimated Callback Hours, Callback Hourly Rate, Callback Material Cost, Total Chemical Cost.
*   **Formulas:**
    *   **Total Labor Cost:** `=Estimated Labor Hours * Hourly Labor Rate`
    *   **Total Callback Cost:** `=(Estimated Callback Hours * Callback Hourly Rate) + Callback Material Cost`
    *   **Total Direct Job Cost:** `=Total Labor Cost + Total Chemical Cost + Other Direct Costs + Total Callback Cost`
    *   **Gross Profit per Job:** `=Total Job Price - Total Direct Job Cost`
    *   **Gross Profit Margin (%):** `=IF(Total Job Price > 0, Gross Profit per Job / Total Job Price, 0)`

### 3. Overhead & Break-Even
Determines the number of jobs required to cover all fixed and variable costs.
*   **Inputs:** Monthly Fixed Costs, Monthly Variable Overhead, Average Direct Cost per Job, Average Revenue per Job.
*   **Formulas:**
    *   **Total Monthly Overhead:** `=Monthly Fixed Costs + Monthly Variable Overhead`
    *   **Contribution Margin per Job:** `=Average Revenue per Job - Average Direct Cost per Job`
    *   **Break-Even Number of Jobs:** `=IF(Contribution Margin per Job > 0, Total Monthly Overhead / Contribution Margin per Job, 0)`
    *   **Break-Even Revenue:** `=Break-Even Number of Jobs * Average Revenue per Job`

### 4. Pricing Strategy ("Are You Undercharging" & Tiered Pricing)
Helps determine if current pricing meets desired margins and generates Good/Better/Best pricing tiers.
*   **Inputs:** Desired Profit Margin (%), Total Estimated Job Cost, Base Price for Good/Better/Best, Markup % for Better Tier, Markup % for Best Tier.
*   **Formulas:**
    *   **Suggested Min Profitable Price:** `=Total Estimated Job Cost / (1 - Desired Profit Margin)`
    *   **Good Tier Price:** `=Base Price`
    *   **Better Tier Price:** `=Base Price * (1 + Markup % for Better Tier)`
    *   **Best Tier Price:** `=Base Price * (1 + Markup % for Best Tier)`

### 5. Equipment ROI
Calculates the return on investment for new equipment purchases.
*   **Inputs:** Purchase Price, Estimated Lifespan (Years), Estimated Maintenance Cost (Annual), Est Revenue Increase/Cost Savings per Job, Average Jobs per Month.
*   **Formulas:**
    *   **Monthly Depreciation:** `=Purchase Price / (Estimated Lifespan * 12)`
    *   **Total Annual Cost of Equipment:** `=(Purchase Price / Estimated Lifespan) + Estimated Maintenance Cost`
    *   **Jobs to Break Even (ROI):** `=IF(Est Revenue Increase > 0, Purchase Price / Est Revenue Increase, 0)`
    *   **Time to Break Even (Months):** `=IF(Average Jobs per Month > 0, Jobs to Break Even / Average Jobs per Month, 0)`

### 6. Employee Compensation
Calculates total labor costs including base pay, commissions, and bonuses.
*   **Inputs:** Base Hourly Rate, Commission Rate (%), Performance Bonus Criteria ($), Job-specific Revenue.
*   **Formulas:**
    *   **Total Labor Cost per Job:** `=(Job Costing!B5 * Base Hourly Rate) + (Job-specific Revenue * Commission Rate) + Performance Bonus`
    *   **Net Profit after Employee Comp:** `=Job-specific Revenue - Total Labor Cost per Job - Job Costing!B15 - Job Costing!B7`

### 7. Drive Time & Setup Allocation
Factors unbillable time into the job cost.
*   **Inputs:** Average Drive Time per Job (mins), Average Setup/Teardown Time per Job (mins), Hourly Rate for Unbillable Time.
*   **Formulas:**
    *   **Total Unbillable Time Cost per Job:** `=((Average Drive Time + Average Setup Time) / 60) * Hourly Rate for Unbillable Time`
    *   **Recommended Adjustment to Job Price:** `=Total Unbillable Time Cost per Job`

### 8. Automated Pricing Data
Estimates labor and chemical costs based on service area size and productivity rates.
*   **Inputs:** Service Area Size (sq ft), Number of Cleaners, Productivity Rate (sq ft/hr/cleaner), Chemical Product Usage Rate (ml/sq ft), Chemical Unit Cost ($/ml), Desired Chemical Markup (%).
*   **Formulas:**
    *   **Estimated Labor Hours:** `=Service Area Size / (Number of Cleaners * Productivity Rate)`
    *   **Estimated Chemical Cost:** `=(Service Area Size * Chemical Product Usage Rate * Chemical Unit Cost) * (1 + Desired Chemical Markup)`
    *   **Suggested Base Price:** `=(B12+B13)/(1-'Pricing Strategy'!B2)`

## Future Enhancements (Not Currently Implemented)
*   **Dynamic Chemical List:** A dropdown list of chemicals with auto-populating unit costs (dynamic features like dropdowns are not implemented, but a detailed breakdown exists in the 'Job Costing' sheet).
*   **Historical Job Logs:** A dedicated sheet for recording and tracking historical job data over time.
*   **Client Retention Rate Tracking:** Monitoring client retention over a period.
*   **Billable Hours Utilization:** Tracking the percentage of billable hours against total paid hours.