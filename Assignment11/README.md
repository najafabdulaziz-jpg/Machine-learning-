**1. Why is this an unsupervised learning problem?**

Because the dataset doesn’t include a target label or any predefined customer groups, no column tells us which segment each customer belongs to. So the algorithm has to find those groups using only the input features—no labels, no hints.

**2. Why did we remove the `CUST_ID` column?**

'CUST_ID' is just an ID. It doesn’t reflect spending, behavior, or anything customers actually do. If you include it, K-Means can get tricked into treating the ID numbers like “distance” signals, even though they’re basically random from a behavior standpoint.

**3. Which columns had missing values?**

When we run 'df.isnull().sum()', missing values show up. 'MINIMUM_PAYMENTS' has about 313 missing entries, and 'CREDIT_LIMIT' has 1. That’s small for CREDIT_LIMIT, but we still need to handle both.

**4. How did you handle the missing values?**

We went with mean imputation—simple and pretty standard (and it keeps things from breaking). Each missing value gets replaced by the mean of its column using 'df.fillna(df.mean(), inplace=True)'. This approach keeps the overall shape of the data fairly similar, instead of pulling extreme values into the mix.

**5. Why is scaling important before applying K-Means?**

K-Means works by measuring distance between points. If one feature has a huge numeric range—say BALANCE or CREDIT_LIMIT in the thousands—it will overpower the distance calculation. Meanwhile, smaller-range features (like frequency columns sitting between  and 1) don’t matter much unless we fix the scale. StandardScaler does that scaling by setting every feature to mean= and std=1, so each one has a fair say.

**6. Which K value did you choose? Explain your answer using the elbow method and silhouette score.**

So we picked **K = 4**.
- **Elbow method:** The inertia falls fast from K=1 to K=3. After K=4, the drop starts slowing down (that bend is the “elbow”). In practice, this suggests that 4 clusters capture most of the structure in the data.
- **Silhouette score:** K=2 gives the top silhouette score, but two clusters are too broad to produce useful segmentation. With K=4, the silhouette score stays solid while the clusters are specific enough to be actionable for business teams.

**7. Based on the cluster summary table, describe each customer segment in your own words.**

| Cluster | Description |
| ------- | ----------- |
| 0 | Low-activity customers — low balance, low purchases, low cash advance. They hardly ever use their card. Chances are, their accounts are inactive (or basically dormant). |
| 1 | High spenders — high balance, high purchases (especially installment purchases), moderate cash advance. These people look loyal and steady, like they shop regularly. Even when they use cash advances, it’s not the main thing. |
| 2 | Cash advance users — high cash advance, low purchases. They lean on the card mainly to borrow cash, not to buy stuff. That pattern usually points to a different kind of need—fast money. |
| 3 | Transactors / Active buyers — moderate-to-high purchases with low balance carried over, which suggests they pay off their balance often. Cash advances are low. So, they’re buying, but they’re not carrying debt. |

**8. Which cluster may represent high-value customers?**

This next group with (high purchases, high credit limit, and high payment amounts) lines up with high-value customers. They use the card for everyday spending, and they also pay their bills, not just sit on balances. Short version: they bring in transaction revenue and they look like a low credit risk.

**9. Which cluster may represent customers who rely more on cash advance?**

Now look at the cluster with high 'CASH_ADVANCE' value and high 'CASH_ADVANCE_FREQUENCY'. That one points to customers who depend on cash advances. They don’t make many regular purchases and instead treat the credit card like a short-term loan (which can hint at financial stress).

**10. How can a company use these clusters for marketing strategy?**

High spenders: Give loyalty rewards, cashback programs, and higher-tier card options so they’ll keep coming back.
Cash advance users: Consider personal loan products or financial advisory services; they may need credit management support.
Low-activity customers: Send re-engagement campaigns, limited-time offers, or bonus points to pull them back into active use.
Transactors: Push no-fee cards or travel perks, because they pay on time and stay low-risk — they’re great fits for premium products.
