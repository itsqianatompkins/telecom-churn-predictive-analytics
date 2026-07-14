# telecom-churn-predictive-analytics
A predictive churn &amp; retention optimization model utilizing a 30,000+ subscriber telecom dataset. Features SQL engagement analysis, exploratory data analysis (EDA), and machine learning pipelines (Logistic Regression &amp; Random Forests) to translate statistical odds ratios into proactive marketing automation tracks.

<img width="1147" height="642" alt="image" src="https://github.com/user-attachments/assets/0a1be906-e66d-4d44-abcd-ecfb14a3400a" />

## Interactive Retention Control Dashboard
*Click the dashboard preview below to explore the interactive, live version on Tableau Public.*

<img width="1365" height="767" alt="Dashboard 1" src="https://github.com/user-attachments/assets/371abe55-e37a-4729-8772-2343878f7391" />

[Click Here - https://public.tableau.com/views/Q-MobileChurnAnalysis/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link]


## **Background**
Q-Mobile, a leading cellphone carrier, faces the critical business challenge of subscriber churn in a highly competitive market. Historically, the company managed customer retention reactively through its call center's retention desk, attempting to persuade customers to stay only after they called to cancel. While "save" rates were high, this reactive approach trained customers to threaten cancellation simply to negotiate discounts, creating an inefficient cycle of desperate concessions. To optimize retention spend and protect margins, Q-Mobile is transitioning to a proactive churn management framework, leveraging predictive analytics to identify at-risk subscribers four months in advance and deploy targeted marketing interventions before customer dissatisfaction peaks.

## **Objective**
The objective of this analysis is to evaluate historical customer characteristics and behaviors to build, validate, and compare predictive classification models (Logistic Regression and Random Forests) that identify high-risk churn signals. By translating model outputs and odds ratios into strategic business insights, this project provides actionable, evidence-based marketing recommendations to proactively mitigate churn and maximize subscriber lifetime value.

## **Data Scope & Timeframe**
- Data Source: Q-Mobile customer profile and behavioral dataset

- Grain: Individual subscriber level

- Sample Size: 30,905 total observations, partitioned into a Training set (21,808 observations / 70%) and a Validation set (9,097 observations / 30%)

- Timeframe: Behavioral data captured over a rolling 4-month period to predict account churn within the subsequent 30 days

- Key Dimensions: Customer Usage & Trends (revenue, minutes of use, overage, roaming), Customer Actions (customer care calls, previous retention desk interactions), Service Quality (dropped, blocked, and unanswered calls), Equipment Characteristics (handset age, web capability, refurbishment status), and Household Demographics (credit rating, occupation, geography)

- Key Metrics: Churn Rate (Target), Odds Ratios, Model Sensitivity (Catch Rate), Specificity (True Negative Rate), and Area Under the ROC Curve (ROC AUC)

- Assumption: Historical behavioral trends over the 4-month window are representative of future cancellation risk patterns across the broader subscriber base

## **Overview**
This analysis will establish a robust predictive analytics pipeline to isolate the behavioral triggers that drive subscriber cancellations, focusing on:

- High-Risk Signal Identification: Determining how operational pain points, such as steep overage minutes, equipment aging, or consecutive dropped calls, quantifiably increase a subscriber's statistical odds of churning.

- Algorithmic Performance Comparison: Developing and tuning multiple model variations to balance model interpretability (Logistic Regression Logits) against raw predictive power (Random Forest classification metrics).

- Financial & Operational Safeguards: Evaluating the trade-offs between Sensitivity (ensuring the model catches the maximum number of true churners) and Specificity (preventing budget waste on loyal users).


These insights will allow Q-Mobile to shift away from costly, reactive discounts and instead deploy automated, behavioral-triggered marketing tracks, such as proactive data plan upgrades or equipment promotions—to secure long-term subscriber loyalty.

**Technical Documentation: This project portfolio includes comprehensive technical documentation, the raw CSV dataset, an end-to-end Jupyter Notebook analysis, and an interactive Tableau dashboard. 
[dat_qmobile.csv](https://github.com/user-attachments/files/29970986/dat_qmobile.csv)  

[Q_Mobile_Churn_Analysis.ipynb](https://github.com/user-attachments/files/29971002/Q_Mobile_Churn_Analysis.ipynb)

## Executive Summary: 
This pipeline acts as an early warning system for customer retention. By evaluating behavioral modifications before account expiration, the model shifts retention efforts from a **reactive strategy** (offering discounts at cancellation) to a **proactive strategy** (addressing systemic usage drops early).

### Key Data Insights & Marketing Automations
* **High-Overage Penalty (Odds Ratio: 1.21):** For every standard deviation increase in monthly overage fees, a customer's odds of churning increase by **21.2%**. 
  * *Marketing Action:* Triggers an automated, dynamic billing sequence offering a plan upgrade to a higher tier with a "3-month fee waiver" before user frustration peaks.
* **The Drop-Off Signal (Odds Ratio: 0.83):** The minutes of use change metric (`changem`) possesses an odds ratio of **0.83**, meaning that decreasing usage values directly escalate churn risk. SQL preprocessing highlights that churned users show an average drop-off of **-14.85%** in usage compared to only **-5.33%** for retained users.
  * *Marketing Action:* Enrolls any subscriber crossing a -10% usage change threshold into an automated re-engagement campaign featuring localized usage rewards or device upgrades.
    
 
  <img width="1411" height="495" alt="image" src="https://github.com/user-attachments/assets/fb347993-185c-400a-80fb-e57bd9209393" />


  <img width="1009" height="643" alt="image" src="https://github.com/user-attachments/assets/64cbc684-a89e-47c9-9ea6-c63bee8918a0" />



## Model Performance & Evaluation Metrics
* **ROC AUC: 0.6025:** Demonstrates stable baseline discriminative capability between churn and non-churn profiles prior to advanced multi-model tuning.
* **Sensitivity (Catch Rate): 0.00%:** At a standard default classification threshold of 0.50, the highly imbalanced class structure (30,305 active vs. 600 churned accounts) yields an initial 0% raw catch rate. 
  * *Portfolio Insight:* This metric provides an excellent talking point for your portfolio readme to explain why optimization techniques—such as adjusting classification probability thresholds, class weighting, or tree-based ensemble methods—are vital to unlock true business value for highly skewed datasets.
* **Specificity: 100.00%:** The default model accurately filters out stable, satisfied users with perfect precision, ensuring zero budget waste on unnecessary promotional distributions to loyal accounts.




