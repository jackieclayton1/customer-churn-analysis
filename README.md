# Project Background
As a data analyst at a telecom provider operating in the U.S. market, my role was to analyze customer churn (cancellations) to identify risks, reduce revenue loss, and improve customer retention. The company has over 7,000 customers with monthly/annual contract options, offering internet, phone, and streaming services. 

Key business metrics include churn rate, average tenure, monthly charges, and total revenue.

Insights and recommendations are provided on the following key areas:

**• Demographics:** gender, age, dependents

**• Account Details:** tenure, contract type, billing, payment method

**• Services:** internet, tech support, online security, streaming

**• Finances:** monthly charges, total revenue lost from churn

The SQL queries used to clean the data and answer various business questions for this analysis can be found [here](https://github.com/jackieclayton1/customer-churn-analysis/blob/main/churn_sql_queries).

An interactive Tableau dashboard used to report and explore sales trends can be found here [link].

# Data Structure & Initial Checks
The company’s database (cleaned to churn_clean) consists of one main customer table with 7,043 records. A description of each column is as follows:

**• Table 1:**

**• Table 2:**

**• Table 3:**

**• Table 4:**

[Entity Relationship Diagram here]

# Executive Summary
### Overview of Findings

This analysis revealed three key takeaways for leadership:

**1. Contract type and tenure are the strongest predictors of customer churn.** Short-term contracts and customers in their first year show the highest churn risk.

**2. Add-on services reduce churn.** Customers with access to online security and tech support services have significantly lower cancellation rates.

**3. Revenue at risk is substantial**. Churned customers account for millions in lost charges annually, but targeted retention could reduce churn by 7-10%, saving acquisition costs.

[Visualization, including a graph of overall trends or snapshot of a dashboard]

# Insights Deep Dive
### Demographics:
**• Seniors Exhibit a Significantly Higher Churn Rate.** Analysis of the customer base shows that senior citizens, defined as aged 65 or older, have a churn rate of 41.68%. This is notably higher than the 23.61% churn rate observed among non-senior customers. This indicates that seniors are a high-risk demographic for churn.

**• Churn Rates Are Nearly Identical Across Genders.** The analysis reveals no significant difference in churn behavior between genders. Male customers have a churn rate of 26.16%, while female customers have a churn rate of 26.91%. The minimal variance suggests that gender is not a contributing factor to customer churn in this dataset.

**• Customers Without Dependents Are Twice as Likely to Churn.** Customers without dependents show a high churn rate of 31.28%. In contrast, customers with dependents are far more loyal, with a churn rate of only 15.48%. This suggests that customers with families have a greater need for stable service and are less likely to switch providers.

[Visualization specific to category 1]

### Account Details:
**• Month-to-Month Contracts Drive the Highest Churn at 42.71%.** The flexibility of month-to-month contracts comes at the cost of loyalty. Customers on this plan have an exceptionally high churn rate of 42.71%. This is in stark contrast to customers on longer-term contracts; the churn rate for one-year contracts is only 11.27%, and for two-year contracts, it drops to a mere 2.83%. This highlights a clear correlation between contract length and customer retention.

**• Electronic Check Payments Are Linked to a 45.26% Churn Rate.** The payment method chosen by a customer is a strong indicator of their likelihood to churn. Customers paying by electronic check have the highest churn rate by a significant margin at 45.26%. Other payment methods show much lower churn: mailed check (19.17%), bank transfer (16.71%), and credit card (15.24%). This suggests a potential dissatisfaction with the e-check process or that it is preferred by less committed customers.

**• Customer Loyalty Solidifies After Two Years, Drastically Reducing Churn.** Customer tenure is a powerful factor in predicting churn. New customers, those with a tenure of less than one year, have the highest churn rate at 47.37%. The rate remains high for customers in the 1-2 year bracket (29.74%). However, a significant drop occurs after the two-year mark, with churn rates falling to 16.98% for the 2-3 year group and continuing to decline as tenure increases.

[Visualization specific to category 2]

### Services:
**• Fiber Optic Customers Churn at Double the Rate of DSL Customers.** While Fiber Optic is a premium service, it is associated with a much higher churn rate of 41.89%. In comparison, customers with DSL service are significantly more loyal, with a churn rate of only 18.96%. This disparity could indicate issues with the Fiber Optic service's price, reliability, or customer support.

**• Lack of Online Security and Tech Support Leads to a 5x Higher Churn Rate.** Customers who do not subscribe to either Online Security or Tech Support services are highly likely to churn, with a rate of 41.87%. Conversely, customers who have both of these protective services are extremely loyal, with a churn rate of only 7.59%. This demonstrates the value of these add-on services in securing customer retention.

**• Streaming Services Do Not Significantly Impact Churn Rates.** The analysis shows that whether a customer subscribes to streaming TV, streaming movies, or both has a negligible impact on their likelihood to churn. Churn rates for all combinations of these services hover between 30% and 34%. This suggests that streaming services are not a key factor in the customer's decision to stay or leave.

[Visualization specific to category 3]

### Finances:
**• Higher Monthly Bills Correlate Directly with Higher Churn.** Analysis of monthly charges reveals a clear trend: as the monthly bill increases, so does the churn rate. Customers paying over $75 per month have the highest churn rate at 35.79%. This is followed by those in the $50-$75 bracket (23.77%), while customers paying under $50 have the lowest churn rate at 19.34%.

**• Churned Customers Account for Over $2.86 Million in Lost Revenue.** The cumulative financial impact of customer churn is substantial. Based on the TotalCharges of all customers who have churned, the total lost revenue amounts to $2,865,823. This figure underscores the critical need to address the key drivers of churn to protect the company's bottom line.

**• Price-Sensitive Customers Show Churn Spikes at Higher Price Tiers.** The data indicates that customers are highly sensitive to price. The churn rate consistently climbs as customers move into higher monthly price tiers. The jump from the sub-$50 bracket to the over-$75 bracket results in an 85% increase in the churn rate, confirming that significant price increases are a major catalyst for customer churn.

[Visualization specific to category 4]

# Recommendations:
Based on the insights and findings above, we would recommend the Customer Success Team to consider the following:

• Month-to-month contracts have a 42.71% churn rate, far higher than annual contracts. **Offer discounts to incentivize customers to switch to annual plans.**

• Customers without access to Online Security and Tech Support services churn 5 times more. **Offer a bundle with support services and/or offer a free trial to demonstrate their value to customers.**

• Fiber Optic customers churn at double the rate of DSL customers. **Investigate the Fiber Optic service for potential issues with reliability.**

• Customers are most likely to churn within their first year. **Implement a proactive, year long customer onboarding program to build customer loyalty.**

# Assumptions and Caveats:
Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

**• Assumption 1:** Blank total charge (TotalCharges) values were treated as missing and set to NULL.

**• Assumption 2:** Revenue loss estimates assume churned customers do not return at any point.
