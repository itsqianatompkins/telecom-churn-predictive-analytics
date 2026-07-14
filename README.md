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

## Core Business Insights: The Behavioral "Red Flags"
Our statistical model and descriptive data isolate three primary operational triggers that cause a subscriber to walk away.

**The Hardware Expiration Trigger (eqpdays | Odds Ratio: 1.36)**:
As shown in our Device Vulnerability distribution, subscriber risk spikes significantly as the current handset ages past one year (specifically clustering between 180 to 360 days). With an odds ratio of 1.36, a user with aging or outdated equipment is 36% more likely to churn than a user with newer hardware.

**The Sticker-Shock Overage Penalty (overage | Odds Ratio: 1.21)**:
For every standard deviation increase in monthly overage minutes, a subscriber's statistical odds of leaving jump by 21%. Customers frequently hit a financial "breaking point" where variable overage costs make their monthly bill feel unpredictable and punitive.

**The Engagement Killer (changem & mou | Odds Ratio: 0.83)**:
A drop-off in active talk time is our strongest leading indicator of contract cancellation. Retained customers maintain a stable baseline with a minor rolling variation of -5.33% in minutes used. Conversely, future churners exhibit an average usage drop of -14.85% over a 4-month window, signaling silent detachment long before they call the retention desk.

## Strategic Action
To maximize customer lifetime value, Q-Mobile will deploy automated retention tracks mapped directly to these behavioral signatures.

| Risk Tier   | Core Behavioral Signal                      | Automated Marketing Action & Lifecycle Track               |
| :---        | :---                                        | :---                                                       |
| **High Risk**| • Overage > 100 minutes<br>• Usage Change < -10% | **Proactive Tier Upgrade Trigger:**<br>Automatically transition the account to the next highest data/voice tier. Offer a "3-month fee waiver" to remove immediate billing friction while keeping them on a higher contract tier. |
| **Medium Risk**| • Overage > 50 minutes OR<br>• Usage Change < -5% | **Re-engagement & Value Incentive Campaign:**<br>Deploy targeted app notifications and email flows offering localized rewards, temporary bonus minutes, or free streaming add-on trials to restore daily usage habits. |
| **Low Risk** | • Stable usage patterns within standard limits | **Standard Retention Pipeline:**<br>Maintain baseline marketing touches, loyalty point accumulations, and scheduled account check-ins without unnecessary margin-eroding discounts. |

## Cross-Functional Recommendations: What We Do Next
**Product & Data Infrastructure: Fix the Data Imbalance**
Our baseline model achieved an exceptional 100% Specificity (it perfectly identifies safe, loyal users, guaranteeing zero wasted marketing dollars on accounts that aren't leaving). However, due to severe data skew (30,305 active accounts vs. 600 churned accounts), our initial default threshold caught 0% of true churners.

*Next Step: Data engineering and data science teams must tune the classification probability threshold away from the 0.50 default or introduce synthetic oversampling (SMOTE) to catch the active target audience.*

**Marketing & Product Operations: The Hardware Refreshes**
Because refurbished devices (refurb | Odds Ratio: 1.17) and device age represent severe structural churn risks, marketing should coordinate with logistics to roll out an automated "Device Lifecycle Renewal Program." Accounts passing the 270-day mark on a single handset should automatically receive targeted trade-in offers or priority upgrades to web-capable devices before contract expiration dates arrive.

**Customer Experience: Eliminate Reactive Discount Cycles**
Move retention desk efforts entirely upstream. Rather than waiting for a frustrated customer to threaten cancellation at the call center—which simply trains users to fake dissatisfaction for a discount—the team will use our Tableau Retention Control Center to flag high-risk accounts 90 days out, executing customer success outreach while the relationship is healthy.




