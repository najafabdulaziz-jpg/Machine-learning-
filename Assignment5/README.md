**Conclusion:**

Accuracy differences across all four settings are tiny (38.8% – 40.3%) with no clear trend.

The best result (top_k = 6, 40.34%) slightly beats the original (top_k = 10, 38.8%), but the differences are small and would likely disappear with different seeds.

The top feature importances remain stable across all top_k settings.

The same set of features dominates in every experiment:
price_per_item → Delivery_Distance_km → GPS coordinates → order_hour → order_dayofweek.

The Item_Name_reduced one-hot columns never reach the top 10, confirming that item identity is not predictive of order outcome.
