Project: A/B Testing — Evaluating the Impact of Marketing Ads on Conversion Rate
1. Project Overview
Project Type: Independent A/B Testing Analysis

Data Source: Kaggle Marketing A/B Testing Dataset

Data Volume: 588,101 user records

Analysis Period: May 2026

Tech Stack: Python (Pandas, Scipy, Statsmodels, Scikit-learn)

2. Business Problem
An e-commerce platform ran an advertising experiment, randomly assigning users into two groups:

Treatment Group (ad): Shown commercial advertisements.

Control Group (psa): Shown public service announcements (placebo).

Core Business Questions:

Does commercial advertising genuinely lift the user purchase conversion rate?

If so, how large is the effect, and when is the optimal time to deliver ads?

3. Experimental Design (The Blueprint)
Before running the analysis, I designed a complete analytical framework to ensure scientific rigor:

Primary Metric: User Conversion Rate (CR).

Core Hypotheses:

H₀ (Null): CR(ad) = CR(psa). The ad has no effect.

H₁ (Alternative): CR(ad) > CR(psa). The ad has a statistically significant positive effect (one-tailed test).

Power Analysis: Calculated the minimum required sample size to ensure the experiment had sufficient sensitivity. Based on a baseline conversion rate of 1.79%, an MDE of 1 percentage point, α = 0.05, and power = 0.80, a minimum of 12,543 users per group was required. The actual sample sizes (ad: 564,577, psa: 23,524) far exceeded this threshold.

4. Analysis Process & Key Findings
I employed a layered statistical analysis approach, moving from the macroscopic to the microscopic, to ensure rigorous conclusions.

4.1 Main Effect: Does the ad work?
Method: One-tailed two-sample z-test for proportions, validated by Bootstrap (10,000 iterations) for robustness.

Result:

Ad group CR: 2.55%

Control group CR: 1.79%

Absolute Lift: 0.77 percentage points (43% relative increase)

Z-statistic: 7.37, P < 0.001

Bootstrap 95% CI: [0.59%, 0.94%], excluding 0.

Conclusion: ✅ Rejected H₀. The commercial ad has a real, statistically significant, and robust positive effect on conversion rate.

4.2 Temporal Analysis: Does the effect vary by day of the week?
Method:

Daily chi-squared tests of independence.

FDR-BH correction to control for false discovery rate from multiple comparisons.

Logistic regression with Likelihood Ratio Test to check for interaction effects between ad type and day of the week.

Result:

Significant lift on Monday, Tuesday, Wednesday, Friday, and Saturday.

No significant lift on Thursday and Sunday.

Interaction effect was significant (P = 0.045), confirming that the ad's effectiveness varies by day.

Conclusion: The ad's impact is not uniform. Optimizing ad delivery based on the day of the week can save budget and improve efficiency.

4.3 Hourly Analysis: What is the golden delivery window?
Method:

Focused on days with significant ad effects.

Built a logistic regression model to predict hourly conversion probability within the ad group.

Result:

Golden Window: 2:00 PM – 5:00 PM, with conversion rates exceeding 3%.

Dead Zone: 1:00 AM – 4:00 AM, with conversion rates below 1.5%.

A secondary evening peak was observed between 8:00 PM and 10:00 PM.

Conclusion: Ad delivery can be optimized down to the hour, concentrating resources on high-efficiency windows.

5. Business Value & Recommendations
Based on this rigorous, multi-layered analysis, I proposed a concrete, data-driven action plan:

Overall Strategy: Maintain the commercial ad strategy as it has a proven, significant effect.

Day-by-Day Optimization: Concentrate spend on high-impact days (Monday, Tuesday, Wednesday, Saturday) and reduce or pause spending on ineffective days (Thursday, Sunday).

Hour-by-Hour Optimization: Allocate the majority of the budget to the 2:00 PM – 5:00 PM golden window, with supplementary spending during the 8:00 PM – 10:00 PM evening peak. Halt spending during the 1:00 AM – 4:00 AM dead zone.

Optimal Combination: The highest potential ROI is expected on Tuesday afternoons between 2:00 PM and 5:00 PM.

6. Limitations & Future Work
Data Gaps: The dataset lacks secondary metrics (e.g., average order value) and guardrail metrics (e.g., total revenue, uninstall rate), limiting a full assessment of the ad's impact on overall business health.

Temporal Context: Specific dates are not provided, making it impossible to control for holidays or other special events.

For the detailed analysis process, please refer to the Jupyter Notebook or the Chinese version of the analysis notes

Ad Frequency: The total ads variable indicates varying ad exposure, which was not the focus of this analysis. Future work could examine the diminishing marginal returns of ad frequency.

Robustness: The interaction effect for day-of-week was near the 0.05 threshold (P=0.045), suggesting a need for replication on larger datasets.

Causal Validity: No A/A test was conducted to rule out randomization failures. Future experiments should incorporate this.
