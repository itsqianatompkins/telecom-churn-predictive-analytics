# telecom-churn-predictive-analytics
A predictive churn &amp; retention optimization model utilizing a 30,000+ subscriber telecom dataset. Features SQL engagement analysis, exploratory data analysis (EDA), and machine learning pipelines (Logistic Regression &amp; Random Forests) to translate statistical odds ratios into proactive marketing automation tracks.

<img width="1147" height="642" alt="image" src="https://github.com/user-attachments/assets/0a1be906-e66d-4d44-abcd-ecfb14a3400a" />

## **Background**
Q-Mobile, a leading cellphone carrier, faces the critical business challenge of subscriber churn in a highly competitive market. Historically, the company managed customer retention reactively through its call center's retention desk, attempting to persuade customers to stay only after they called to cancel. While "save" rates were high, this reactive approach trained customers to threaten cancellation simply to negotiate discounts, creating an inefficient cycle of desperate concessions. To optimize retention spend and protect margins, Q-Mobile is transitioning to a proactive churn management framework, leveraging predictive analytics to identify at-risk subscribers four months in advance and deploy targeted marketing interventions before customer dissatisfaction peaks.

## **Objective**
The objective of this analysis is to evaluate historical customer characteristics and behaviors to build, validate, and compare predictive classification models (Logistic Regression and Random Forests) that identify high-risk churn signals. By translating model outputs and odds ratios into strategic business insights, this project provides actionable, evidence-based marketing recommendations to proactively mitigate churn and maximize subscriber lifetime value.

## Interactive Retention Control Dashboard
*Click the dashboard link below to explore the interactive, live version on Tableau Public.*

<img width="1365" height="767" alt="Dashboard 1" src="https://github.com/user-attachments/assets/371abe55-e37a-4729-8772-2343878f7391" />

[Click Here - https://public.tableau.com/views/Q-MobileChurnAnalysis/Dashboard1?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link]


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

## Executive Summary
This predictive pipeline serves as an early warning system for subscriber retention. By isolating behavioral friction points up to 90 days before account expiration, the framework shifts operations from a reactive retention model (issuing discounts at the call center) to a proactive, automated intervention strategy.

### Operational Insights & Marketing Automations
* **Overage Fee Exposure (Odds Ratio: 1.21):** For every standard deviation increase in monthly overage fees, a customer's odds of churning increase by 21.2%. 
  * *Action:* Triggers an automated billing sequence offering a seamless transition to a higher tier plan alongside a temporary three-month fee waiver before billing frustration peaks.
* **Usage Contraction (Odds Ratio: 0.83):** Decreasing minutes of use (`changem`) serves as the strongest leading indicator of cancellation. SQL preprocessing shows that future churners exhibit an average 14.85% usage drop over a four-month rolling window, compared to just a 5.33% drop for active users.
  * *Action:* Enrolls subscribers crossing a 10% usage drop threshold into targeted re-engagement campaigns featuring dynamic account incentives or hardware upgrade credits.

## Model Performance & Operational Safeguards
* **ROC AUC:** 0.6025
* **Sensitivity (Catch Rate):** 0.00% (At the default 0.50 probability threshold). The highly skewed target distribution (30,305 active vs. 600 churned accounts) requires localized threshold tuning or synthetic oversampling (SMOTE) to capture the target audience before deployment.
* **Specificity:** 100.00% (The model filters out stable, low-risk users with perfect precision, protecting marketing margins from unnecessary promotional distributions).

  <img width="1411" height="495" alt="image" src="https://github.com/user-attachments/assets/fb347993-185c-400a-80fb-e57bd9209393" />

  <img width="1009" height="643" alt="image" src="https://github.com/user-attachments/assets/64cbc684-a89e-47c9-9ea6-c63bee8918a0" />


## Core Business Insights:
Our statistical model and descriptive data isolate three primary operational triggers that cause a subscriber to walk away.

**The Hardware Expiration Trigger (eqpdays | Odds Ratio: 1.36)**:
As shown in our Device Vulnerability distribution, subscriber risk spikes significantly as the current handset ages past one year (specifically clustering between 180 to 360 days). With an odds ratio of 1.36, a user with aging or outdated equipment is 36% more likely to churn than a user with newer hardware.

**The Overage Penalty (overage | Odds Ratio: 1.21)**:
For every standard deviation increase in monthly overage minutes, a subscriber's statistical odds of leaving jump by 21%. Customers frequently hit a financial "breaking point" where variable overage costs make their monthly bill feel unpredictable and punitive.

**The Engagement Discrepancy (changem & mou | Odds Ratio: 0.83)**:
A drop-off in active talk time is our strongest leading indicator of contract cancellation. Retained customers maintain a stable baseline with a minor rolling variation of -5.33% in minutes used. Conversely, future churners exhibit an average usage drop of -14.85% over a 4-month window, signaling silent detachment long before they call the retention desk.

## Subscriber Retention Insights & Action Plan

### Core Behavioral Risks
1. **Device Longevity (Odds Ratio: 1.36):** Risk increases sharply as a handset passes the 180-to-360-day mark[cite: 1]. Subscribers holding older equipment are **36% more likely to churn** than users with newer hardware[cite: 1]. If the handset is refurbished (Odds Ratio: 1.17), the odds of churning increase by **17%**[cite: 1].
2. **Predictable Billing Outliers:** Variable monthly overage charges create an erratic billing experience that directly drives cancellation spikes[cite: 1].
3. **Silent Account Detachment:** Active conversation volume drops significantly months before explicit cancellation occurs, making account contraction the primary leading indicator of customer friction[cite: 1].

### Strategic Action Matrix
To maximize customer lifetime value, Q-Mobile will deploy automated retention tracks mapped directly to these behavioral signatures[cite: 1].

| Risk Tier | Core Behavioral Signal | Automated Marketing Action & Lifecycle Track |
| :--- | :--- | :--- |
| **High Risk** | • Overage > 100 minutes<br>• Usage Change < -10% | **Proactive Tier Upgrade Trigger:**<br>Automatically transition the account to the next highest data/voice tier. Offer a "3-month fee waiver" to remove immediate billing friction while keeping them on a higher contract tier. |
| **Medium Risk** | • Overage > 50 minutes OR<br>• Usage Change < -5% | **Re-engagement & Value Incentive Campaign:**<br>Deploy targeted app notifications and email flows offering localized rewards, temporary bonus minutes, or free streaming add-on trials to restore daily usage habits. |
| **Low Risk** | • Stable usage patterns within standard limits | **Standard Retention Pipeline:**<br>Maintain baseline marketing touches, loyalty point accumulations, and scheduled account check-ins without unnecessary margin-eroding discounts. |

## Cross-Functional Recommendations

### Product & Data Infrastructure
* **Optimize Data Architecture Pipeline:** Direct the data science team to shift modeling weights or adjust classification cut-off limits away from the default 0.50 threshold. While the baseline model yields 100% specificity (ensuring zero wasted marketing spend on loyal accounts), the severe class skew (30,305 active vs. 600 churned accounts) resulted in an initial 0% raw catch rate. To resolve this imbalance and capture the target audience, next-step technical implementations must integrate synthetic oversampling (SMOTE) or probability threshold tuning before production deployment.

### Marketing & Product Operations
* **Implement a Device Lifecycle Renewal Program:** Coordinate marketing and supply chain logistics to trigger automated hardware replacement cycles for accounts crossing the 270-day handset threshold. Because refurbished devices (Odds Ratio: 1.17) and overall equipment age represent high-risk churn indicators, accounts with aging hardware should automatically receive targeted trade-in incentives or priority upgrades to modern, web-capable devices before contract expiration.

### Customer Experience
* **Upstream Retention Desk Operations:** Transition customer retention workflows away from reactive discount negotiations at the call center—a process that trains customers to threaten cancellation simply to secure cheaper rates. Instead, leverage the visual metrics within the Tableau Retention Control Center to run proactive customer success outreach 90 days prior to contract conclusions, resolving customer friction while the account relationship is still highly salvageable.```

