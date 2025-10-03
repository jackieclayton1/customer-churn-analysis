# DATA CLEANING PROCESS #
-- This query identifies and removes duplicate customer records 
-- from the churn_clean table based on the customerID column.

-- Define a Common Table Expression (CTE) to find duplicate customer IDs.
WITH DuplicatesCTE AS (
    SELECT
        customerID,
        -- Assign a unique row number to each record within a group of the same customerID.
        -- If a customerID appears more than once, the second instance will get RowNum = 2, the third will get RowNum = 3, and so on.
        ROW_NUMBER() OVER (
            PARTITION BY customerID
            ORDER BY customerID    
        ) AS RowNum
    FROM
        churn_clean
)
DELETE churn_clean
FROM
    churn_clean
-- Join the original table with our CTE to link the RowNum to the actual table rows.
JOIN
    DuplicatesCTE ON churn_clean.customerID = DuplicatesCTE.customerID
-- The DELETE operation will only affect rows where the RowNum is greater than 1, which are the duplicates.
WHERE
    DuplicatesCTE.RowNum > 1;

# CHURN BY DEMOGRAPHICS #

-- Calculate churn rate by gender
SELECT
    Gender,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    Gender
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate for senior citizens (aged 65 or older) vs. non-seniors
SELECT
    SeniorCitizen,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    SeniorCitizen
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate based on whether a customer has a partner
SELECT
    Partner,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    Partner
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate based on whether a customer has dependents
SELECT
    Dependents,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    Dependents
ORDER BY
    Churn_Percentage DESC;

# CHURN BY ACCOUNT DETAILS #

-- Calculate churn rate by customer tenure, grouped into yearly brackets
SELECT
    CASE
        WHEN tenure <= 12 THEN 'Less than 1 Year'
        WHEN tenure <= 24 THEN '1-2 Years'
        WHEN tenure <= 36 THEN '2-3 Years'
        WHEN tenure <= 48 THEN '3-4 Years'
        WHEN tenure <= 60 THEN '4-5 Years'
        WHEN tenure <= 72 THEN '5-6 Years'
        ELSE '6+ Years'
    END AS Tenure_Group,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    Tenure_Group
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate by contract type
SELECT
    Contract,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    Contract
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate by payment method
SELECT
    PaymentMethod,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    PaymentMethod
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate based on paperless billing status
SELECT
    PaperlessBilling,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    PaperlessBilling
ORDER BY
    Churn_Percentage DESC;

# CHURN BY SERVICES #

-- Calculate churn rate by Internet Service type
SELECT
    InternetService,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
WHERE
    InternetService IN ('DSL', 'Fiber optic') -- Filter for customers only with internet service
GROUP BY
    InternetService
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate based on Online Security and Tech Support subscriptions
SELECT
    OnlineSecurity,
    TechSupport,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
WHERE
    OnlineSecurity != 'No internet service' AND TechSupport != 'No internet service' -- Filter for customers only with internet service
GROUP BY
    OnlineSecurity, TechSupport
ORDER BY
    Churn_Percentage DESC;

-- Calculate churn rate based on streaming service subscriptions
SELECT
    StreamingTV,
    StreamingMovies,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
WHERE
    StreamingTV != 'No internet service' AND StreamingMovies != 'No internet service' -- Filter for customers only with internet service
GROUP BY
    StreamingTV, StreamingMovies
ORDER BY
    Churn_Percentage DESC;

# CHURN BY FINANCIALS #

-- Calculate total revenue lost from churned customers
SELECT
    SUM(TotalCharges) AS Revenue_Churned
FROM
    churn_clean
WHERE
    Churn LIKE '%Yes%';

-- Calculate churn rate based on customer monthly price brackets
SELECT
    CASE
        WHEN MonthlyCharges < 50 THEN 'Under $50'
        WHEN MonthlyCharges <= 75 THEN '$50 - $75'
        ELSE 'Over $75'
    END AS Customer_Price_Demographic,
    COUNT(CustomerID) AS Total_Customers,
    SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) AS Churned_Customers,
    (SUM(CASE WHEN Churn LIKE '%Yes%' THEN 1 ELSE 0 END) * 100.0 / COUNT(CustomerID)) AS Churn_Percentage
FROM
    churn_clean
GROUP BY
    Customer_Price_Demographic
ORDER BY
    Churn_Percentage DESC;
