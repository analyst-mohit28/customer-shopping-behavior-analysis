# Customer Shopping Behavior Analysis  

## Business Problem

E-commerce businesses often struggle to understand:
- Which customer segments generate the most revenue
- Whether discounts impact profitability
- If subscription programs increase long-term value
- How age and loyalty influence purchasing behavior

This project analyzes 3,900 customer transactions to uncover revenue drivers and customer patterns.

---

## Key Performance Indicators (KPIs)

- **Total Revenue:** 233,081
- **Total Customers:** 3,900
- **Average Order Value (AOV):** 59.76
- **Male Revenue Contribution:** 67.7%
- **Female Revenue Contribution:** 32.3%

---

## Tools Used

- Python (Pandas, NumPy)
- MySQL
- Power BI

---

## Data Preparation (Python)

- Handled missing review ratings using median imputation
- Standardized column naming (snake_case)
- Created new feature: `age_group`
- Created customer segmentation (New / Returning / Loyal)
- Loaded cleaned dataset into MySQL for structured analysis

---

## SQL Business Analysis

### Revenue by Gender

```sql
SELECT gender, SUM(purchase_amount) AS total_revenue
FROM customers
GROUP BY gender;
```

Insight:
Male customers contribute nearly 2.1x more revenue than female customers.

---

### Subscription vs Non-Subscription Revenue

```sql
SELECT subscription_status, SUM(purchase_amount)
FROM customers
GROUP BY subscription_status;
```

Insight:
Subscribers do not significantly outperform non-subscribers in average spending, indicating weak subscription monetization.

---

### Discount Dependency

```sql
SELECT product_name,
       COUNT(CASE WHEN discount_applied = 'Yes' THEN 1 END) * 100.0 / COUNT(*) AS discount_rate
FROM customers
GROUP BY product_name
ORDER BY discount_rate DESC
LIMIT 5;
```

Insight:
Certain products show heavy discount dependency, posing potential margin risk.

---

## Dashboard Insights (Power BI)

The interactive dashboard highlights:

- Revenue distribution by gender
- Customer loyalty segmentation
- Age group revenue contribution
- Subscription impact
- Discount-dependent products

## Dashboard Preview

![Dashboard Overview](https://github.com/analyst-mohit28/customer-shopping-behavior-analysis/blob/main/Dashboard.png)

---

## Business Insights

- Revenue is highly gender-skewed (68% male contribution).
- Average order value remains moderate at 59.76.
- Loyal customers dominate the customer base.
- Subscription model does not significantly increase average spending.
- Some products rely heavily on discounts, reducing potential margins.

---

## Strategic Recommendations

1. Target high-spending male segment with personalized retention campaigns.
2. Improve subscription incentives to increase recurring revenue.
3. Reduce over-reliance on discount-heavy products.
4. Develop targeted acquisition strategies for underperforming segments.

---

## Conclusion

This project demonstrates a full analytics workflow:

Data Cleaning → Feature Engineering → SQL Analysis → Dashboard Visualization → Business Strategy

It showcases the ability to transform raw transaction data into actionable business insights.
