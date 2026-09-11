# A/B Testing — Recommendation System

A business-focused evaluation of an A/B experiment designed to test whether a new recommendation system improved conversion across an online-store funnel.

## About the Project

An international online store introduced an improved recommendation system and launched the `recommender_system_test` to evaluate its effect on new users.

The expected outcome was ambitious: **Group B needed to achieve at least a 10% relative increase in conversion at each of the main funnel stages** within 14 days of registration.

The analysis therefore goes beyond comparing conversion rates. I also evaluate whether the experiment itself was executed well enough to support a reliable product decision.

## Business Question

**Should the company launch the new recommendation system based on the results of this experiment?**

To answer that question, I evaluated:

1. whether the experiment followed its technical specification;
2. whether the analytical sample was clean and comparable;
3. conversion through `product_page`, `product_cart`, and `purchase`;
4. statistical significance using two-proportion Z-tests;
5. whether the required +10% business uplift was achieved;
6. whether data-quality and experiment-design issues affected the reliability of the result.

## Tools & Technologies

- Python
- pandas
- NumPy
- Matplotlib
- SciPy
- Jupyter Notebook
- A/B Testing
- Conversion Funnel Analysis
- Hypothesis Testing
- Experiment Design

## Experiment Specification

The experiment was expected to:

- run from **7 December 2020 to 1 January 2021**;
- stop accepting new participants after **21 December 2020**;
- include approximately **6,000 participants**;
- include **15% of new EU users**;
- compare **Group A (control)** with **Group B (test)**;
- measure key behaviour within **14 days of registration**;
- deliver at least **+10% relative improvement** in `product_page`, `product_cart`, and `purchase` conversion.

## Analysis Approach

The project followed six main stages:

1. **Data-quality review** — checking types, missing values, duplicates, and date ranges.
2. **Experiment validation** — reviewing sample size, region, group allocation, and overlap with another experiment.
3. **Analytical sample preparation** — restricting the analysis to eligible EU users and removing contaminated participants.
4. **Funnel analysis** — comparing conversion at the main product stages.
5. **Statistical testing** — applying two-proportion Z-tests with a Bonferroni correction.
6. **Robustness analysis** — repeating the comparison on an earlier cohort with more complete observation.

## Experiment Quality Findings

The test was not executed exactly as planned.

- **3,675 participants** were included instead of approximately 6,000.
- **3,481 participants** were from the EU.
- Observed participation among eligible new EU users was **8.82%**, below the planned 15%.
- **887 participants** also appeared in another experiment.
- After removing overlapping users, the final analytical sample contained **2,594 users**.
- Group allocation was strongly unbalanced:
  - **A: 1,939 users**
  - **B: 655 users**
- Event coverage was incomplete:
  - no events were recorded on **25 December**;
  - only **89 events** were recorded on **30 December**;
  - the dataset ended before the planned experiment end date.
- The **Christmas & New Year Promo** overlapped with part of the test period.

These limitations reduce confidence in a strong causal interpretation.

## Funnel Results

| Funnel stage | Group A | Group B | Relative lift B vs A |
|---|---:|---:|---:|
| Product page | 65.24% | 56.03% | -14.12% |
| Product cart | 30.38% | 28.09% | -7.52% |
| Purchase | 31.61% | 29.16% | -7.76% |

Group B did **not** achieve the required +10% improvement in any main stage.

Instead, observed conversion was lower across all three metrics.

## Statistical Results

I used a two-sided Z-test for two independent proportions.

Because three related tests were performed, I also considered a Bonferroni-adjusted significance level of approximately **0.0167**.

### `product_page`

- **p-value ≈ 0.000025**
- statistically significant under both thresholds;
- difference favours **Group A**, not Group B;
- Group B conversion is approximately **9.21 percentage points lower**.

### `product_cart`

- **p-value ≈ 0.269**
- no statistically significant difference.

### `purchase`

- **p-value ≈ 0.240**
- no statistically significant difference.

The only statistically clear effect is therefore a **negative result for Group B at the product-page stage**.

## Robustness Check

To reduce the impact of incomplete end-of-period event coverage, I repeated the funnel comparison using users who registered by **10 December 2020**.

This smaller cohort contained:

- **275 users in A**
- **238 users in B**

Observed relative lifts for Group B were:

- `product_page`: **-8.10%**
- `product_cart`: **+1.30%**
- `purchase`: **+3.85%**

None of these differences was statistically significant, and Group B still failed to achieve the required +10% improvement across all stages.

The business conclusion therefore remained unchanged.

## Business Recommendation

**I do not recommend launching the new recommendation system based on this experiment.**

The new experience failed to achieve the required business uplift and the only statistically significant difference was negative for Group B.

At the same time, the experiment contains meaningful design and data-quality limitations. Because of this, I would also avoid concluding that the recommendation system is definitively worse.

### Recommended next steps

- repeat the experiment without users participating in another simultaneous test;
- reach the planned sample size;
- use a more balanced A/B allocation;
- guarantee a complete 14-day observation window for all participants;
- validate event tracking before and during the experiment;
- avoid major promotional periods where possible, or control for them explicitly.

## What I Learned

What I found most valuable in this project was seeing why a good A/B test is about much more than calculating a p-value.

Experiment design, participant allocation, observation windows, overlapping campaigns, and data quality all influence whether a result is reliable enough to support a real business decision.

This project strengthened my ability to connect statistical analysis with practical judgement — asking not only **“Is the result significant?”**, but also **“Is this experiment trustworthy enough to act on?”**

## Executive Presentation

I also prepared a short executive presentation summarising the main findings, risks, and recommendation.

👉 **[View the executive presentation](https://acrobat.adobe.com/id/urn:aaid:sc:EU:c79b274f-bd8f-4e16-930a-e8f9392ecfee)**
