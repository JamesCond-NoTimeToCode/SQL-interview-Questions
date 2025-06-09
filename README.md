Identify customers who made purchases on exactly three different days in the last month from the table "Purchases (customer_id, Purchase_Date)"

Answer: 
WITH purchases_summary AS (
SELECT  customer_id, COUNT(DISTINCT Purchase_date) as Purchase_days 
FROM Purchases 
WHERE purchase_date >= DATEADD(month, -1, CURRENT_DATE)
GROUP BY customer_id
)
select customer_id 
from Purchases_summary 
WHERE purchase_days = 3;
