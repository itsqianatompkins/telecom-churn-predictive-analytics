# telecom-churn-predictive-analytics
A predictive churn &amp; retention optimization model utilizing a 30,000+ subscriber telecom dataset. Features SQL engagement analysis, exploratory data analysis (EDA), and machine learning pipelines (Logistic Regression &amp; Random Forests) to translate statistical odds ratios into proactive marketing automation tracks.

<img width="1147" height="642" alt="image" src="https://github.com/user-attachments/assets/0a1be906-e66d-4d44-abcd-ecfb14a3400a" />

**Background**
Q-Mobile, a leading cellphone carriers, faces the critical business challenge of subscriber churn in a highly competitive market. Historically, the company managed customer retention reactively through its call center's retention desk, attempting to persuade customers to stay only after they called to cancel. While "save" rates were high, this reactive approach trained customers to threaten cancellation simply to negotiate discounts, creating an inefficient cycle of desperate concessions. To optimize retention spend and protect margins, Q-Mobile is transitioning to a proactive churn management framework, leveraging predictive analytics to identify at-risk subscribers four months in advance and deploy targeted marketing interventions before customer dissatisfaction peaks.

**Objective**
The objective of this analysis is to evaluate historical customer characteristics and behaviors to build, validate, and compare predictive classification models (Logistic Regression and Random Forests) that identify high-risk churn signals. By translating model outputs and odds ratios into strategic business insights, this project provides actionable, evidence-based marketing recommendations to proactively mitigate churn and maximize subscriber lifetime value.

**Data Scope & Timeframe**
--Data Source: Q-Mobile customer profile and behavioral dataset

--Grain: Individual subscriber level

--Sample Size: 30,905 total observations, partitioned into a Training set (21,808 observations / 70%) and a Validation set (9,097 observations / 30%)

--Timeframe: Behavioral data captured over a rolling 4-month period to predict account churn within the subsequent 30 days

--Key Dimensions: Customer Usage & Trends (revenue, minutes of use, overage, roaming), Customer Actions (customer care calls, previous retention desk interactions), Service Quality (dropped, blocked, and unanswered calls), Equipment Characteristics (handset age, web capability, refurbishment status), and Household Demographics (credit rating, occupation, geography)

--Key Metrics: Churn Rate (Target), Odds Ratios, Model Sensitivity (Catch Rate), Specificity (True Negative Rate), and Area Under the ROC Curve (ROC AUC)

--Assumption: Historical behavioral trends over the 4-month window are representative of future cancellation risk patterns across the broader subscriber base

**Overview**
This analysis will establish a robust predictive analytics pipeline to isolate the behavioral triggers that drive subscriber cancellations, focusing on:
--High-Risk Signal Identification: Determining how operational pain points—such as steep overage minutes, equipment aging, or consecutive dropped calls—quantifiably increase a subscriber's statistical odds of churning.
--Algorithmic Performance Comparison: Developing and tuning multiple model variations to balance model interpretability (Logistic Regression Logits) against raw predictive power (Random Forest classification metrics).
--Financial & Operational Safeguards: Evaluating the trade-offs between Sensitivity (ensuring the model catches the maximum number of true churners) and Specificity (preventing budget waste on loyal users).

These insights will allow Q-Mobile to shift away from costly, reactive discounts and instead deploy automated, behavioral-triggered marketing tracks—such as proactive data plan upgrades or equipment promotions—to secure long-term subscriber loyalty.
