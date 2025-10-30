# Project Background
As a data analyst at a telecom provider operating in the U.S. market, an in depth analysis was conducted to evaluate customer churn (cancellations) to identify risks, reduce revenue loss, and improve customer retention. The company has over 7,000 customers with monthly/annual contract options, offering internet, phone, and streaming services. 

Key business metrics include churn rate, average tenure, monthly charges, and total revenue.

Insights and recommendations are provided on the following key areas: demographics, account details, add-on services, and finances.

The SQL queries used to clean the data and answer various business questions for this analysis can be found [here](https://github.com/jackieclayton1/customer-churn-analysis/blob/main/churn_queries.sql).

# Executive Summary
### Overview of Findings

This analysis revealed three key takeaways for leadership:

**1. Contract type and tenure are the strongest predictors of customer churn.** Short-term contracts and customers in their first year show the highest churn risk.

**2. Add-on services reduce churn.** Customers with access to online security and tech support services have significantly lower cancellation rates.

**3. Revenue at risk is substantial**. Churned customers account for millions in lost charges annually, but targeted retention could reduce churn by 7-10%, saving millions in acquisition costs.

![alt_text](images/Screenshot%202025-10-29%20224703.png)

# Insights Deep Dive
### Demographics:
![alt_text](images/Screenshot%202025-10-28%20211133.png)
**• Seniors Exhibit a Significantly Higher Churn Rate.** Analysis of the customer base shows that senior citizens, defined as aged 65 or older, have a churn rate of 42%. This is notably higher than the churn rate observed among non-senior customers. This indicates that seniors are a high-risk cancellation demographic

![alt_text](images/Screenshot%202025-10-29%20221640.png)
**• Churn Rates Are Nearly Identical Across Genders.** The analysis reveals no significant difference in churn behavior between genders. The minimal variance suggests that gender is not a contributing factor to customer churn.

### Account Details:
![alt_text](images/Screenshot%202025-10-29%20213557.png)
**• Month-to-Month Contracts Drive the Highest Churn.** The flexibility of month-to-month contracts comes at the cost of loyalty. Customers on this plan have an exceptionally high churn rate. This is in stark contrast to customers on longer-term contracts; for two-year contracts, it drops to a mere 3%. This highlights a clear correlation between contract length and customer retention.

![alt_text](images/Screenshot%202025-10-29%20213532.png)
**• Customer Loyalty Solidifies After Two Years, Drastically Reducing Churn.** Customer tenure is a powerful factor in predicting churn. New customers, those with a tenure of less than one year, have the highest churn rate. The rate remains high for customers in the 1-2 year bracket. However, a significant drop occurs after the two-year mark, with churn rates falling for the 2-3 year group and continuing to decline as tenure increases.

### Services:
![alt_text](images/Screenshot%202025-10-29%20221651.png)
**• Fiber Optic Customers Churn at Double the Rate of DSL Customers.** While Fiber Optic is a premium service, it is associated with a much higher churn rate. In comparison, customers with DSL service are significantly more loyal, with lower churn rate. This disparity could indicate issues with the Fiber Optic service's price, reliability, or customer support.

![alt_text](images/Screenshot%202025-10-29%20213445.png)
**• Lack of Online Security and Tech Support Leads to a 5x Higher Churn Rate.** Customers who do not subscribe to either Online Security or Tech Support services are highly likely to churn. Conversely, customers who have both of these protective services are extremely loyal, with a much lower churn rate. This demonstrates the value of these add-on services in securing customer retention.

### Finances:
![alt_text](images/Screenshot%202025-10-29%20213618.png)
**• Higher Monthly Bills Correlate Directly with Higher Churn.** Analysis of monthly charges reveals a clear trend: as the monthly bill increases, so does the churn rate. Customers paying over $75 per month have the highest churn rate. This is followed by those in the $50-$75 bracket, while customers paying under $50 have the lowest churn rate.

**• Churned Customers Account for Over $2.86 Million in Lost Revenue.** The cumulative financial impact of customer churn is substantial. Based on the total charges of all customers who have churned, the total lost revenue amounts to $2,862,823. This figure underscores the critical need to address the key drivers of churn to protect the company's bottom line.

# Recommendations:
Based on the insights and findings above, we would recommend the Customer Success Team to consider the following:

• Month-to-month contracts have a 43% churn rate, far higher than annual contracts. **Offer discounts to incentivize customers to switch to annual plans.**

• Customers without access to Online Security and Tech Support services churn 5 times more. **Offer a bundle with support services and/or offer a free trial to demonstrate their value to customers.**

• Fiber Optic customers churn at double the rate of DSL customers. **Investigate the Fiber Optic service for potential issues with reliability.**

• Customers are most likely to churn within their first year. **Implement a proactive, year long customer onboarding program to build customer loyalty.**

# Assumptions and Caveats:
Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

**• Assumption 1:** Blank total charge (TotalCharges) values were treated as missing and set to NULL.

**• Assumption 2:** Revenue loss estimates assume churned customers do not return at any point.
