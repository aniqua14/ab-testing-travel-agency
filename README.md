# A/B Testing Analysis — Online Travel Agency Search Ranking System

This project presents a full end-to-end A/B test analysis conducted for an online travel agency (OTA) evaluating whether a new search ranking algorithm should be rolled out to all users. The analysis covers experiment validation, statistical hypothesis testing, effect size estimation, and a final data-driven business recommendation.

## Business Context

The Product team developed a new search ranking system aimed at improving conversion rates — the proportion of sessions that end with a booking. Before a full rollout, they needed statistical evidence that the new system performs better without negatively affecting the user experience. Two key metrics were evaluated: conversion rate as the primary metric and time to booking as a guardrail metric.

## Dataset

The analysis uses two session-level and user-level datasets provided by the Product team. The sessions dataset contains 16,981 records with booking timestamps, time to booking in minutes, and session identifiers. The users dataset contains experiment group assignments (control or variant) for all logged-in users. After merging and cleaning, 15,283 usable sessions were retained for analysis.

## Methodology

The project follows a structured experiment evaluation pipeline. First, the conversion column was engineered from booking timestamp data. The two datasets were then merged on user ID to assign experiment groups to each session. A Chi-Square test was performed to validate the 50/50 control-variant split and confirm no Sample Ratio Mismatch (SRM) existed. A one-tailed Z-test was used to assess the statistical significance of the conversion rate difference between groups. A two-tailed T-test was applied to the time to booking metric to check whether the guardrail was affected. Finally, Average Treatment Effect (ATE) was calculated for both metrics.

## Key Results

| Metric | Control | Variant | Effect Size | P-Value | Significant |
|--------|---------|---------|-------------|---------|-------------|
| Conversion Rate | 15.92% | 18.19% | +14.22% | 0.0001 | Yes |
| Time to Booking | 15.01 min | 14.89 min | -0.79% | 0.5365 | No |

## Recommendation

Both rollout criteria were met. The new search ranking system delivers a statistically significant 14.22% relative improvement in conversion rate and does not negatively impact time to booking. The recommendation is to proceed with a full production rollout.

## Technologies Used

Python, Pandas, SciPy, Pingouin, Statsmodels
