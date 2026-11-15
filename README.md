# QuickBite Customer Value Analysis

Exploratory data analysis of 2,000 food-delivery customers: cleaning messy data, understanding how customers spend, and finding which attributes are linked to higher annual spend.

**Tools:** Python, pandas, NumPy, Matplotlib, Seaborn, SciPy

## Business problem
QuickBite is a food-delivery startup in 10 Indian cities. Leadership noticed that revenue seemed to come from a small group of heavy users, that delivery times felt inconsistent, and that the customer data had gaps and obvious errors. The goal was to clean the data, understand it, and report what drives customer spending.

## Dataset
- 2,000 customers, 18 columns (demographics, city tier, membership, app usage, delivery time, order value, rating, orders and annual spend)
- Synthetic data built to behave like real delivery data, including planted missing values and errors

## What I did
1. **Data inspection:** checked missing values (6 columns, 4% to 13% missing) and spotted impossible values such as ages of 0 and 150.
2. **Outlier treatment:** compared the IQR and Z-score rules and treated 11 clearly wrong values (3 ages, 4 delivery times, 4 order values) as errors. High spenders were kept because they are genuine customers.
3. **Missing value imputation:** used medians (group medians by city tier for order value and rating) and an "Unknown" category for gender. Compared distributions before and after with KDE plots.
4. **Distributions:** histograms, KDE plots and skewness for age, rating, delivery time, order value, spend and orders. Showed order value is log-normal.
5. **Relationships:** covariance, correlation heatmap, scatter plots, line plots and box plots by group.
6. **Encoding:** label, one-hot and target encoding, with a discussion of the dummy variable trap and leakage.
7. **Central tendency and percentiles:** mean, median, mode and P10 to P99.
8. **Revenue concentration:** Pareto analysis and the 80/20 rule.
9. **PDF and CDF:** probability of long delivery waits.

## Key findings
- **Revenue is concentrated.** The top 20% of customers generate **60.6% of revenue**, and about 12% of customers generate half of it. It is strong concentration, but weaker than the classic 80/20 rule.
- **The average is misleading.** Mean annual spend is about 13,000 INR, but the median is about **7,100 INR**, because a few heavy users pull the mean up.
- **Order frequency matters most.** Orders in the last 12 months has the strongest correlation with annual spend (**r = 0.72**), followed by average order value (r = 0.25). Other variables show almost no link.
- **Membership:** median spend rises from about 5,900 INR (Basic) to 12,400 INR (Platinum), but 59% of customers are on Basic.
- **Delivery:** the median delivery takes 32 minutes, 90% arrive within about 49 minutes, and about **1 in 6 customers (15.6%) waits more than 45 minutes**. Lower-tier cities are slower (median 36.6 minutes in Tier 3 vs 30.6 in Tier 1).
- **Missing ratings are not random.** Customers who left no rating waited about 8 minutes longer on average, so the average rating probably overstates satisfaction.

## Recommendations
1. Protect the top 20% of customers with retention perks, and test frequency-based offers to move mid-spending customers to order more often.
2. Focus delivery improvements on Tier 2 and Tier 3 cities, and ask for feedback after every delivery over 45 minutes.

## Limitations
- Correlation does not prove causation (for example, membership level and spend may influence each other).
- About 13% of ratings were imputed with medians, which can hide a real link between slow delivery and low ratings.
- The data is synthetic, so the results illustrate the method rather than describe a real company.

## Repository contents
| File | Description |
|---|---|
| `QuickBite_Customer_Analysis.ipynb` | Full analysis with explanations and 30 charts |
| `quickbite_customers.csv` | Raw dataset |
| `quickbite_clean.csv` | Cleaned dataset (no missing values) |

## How to run
1. Download this repository into one folder.
2. Install the libraries: `pip install pandas numpy matplotlib seaborn scipy`
3. Open `QuickBite_Customer_Analysis.ipynb` in Jupyter or Google Colab and run all cells.

## Author
Ruchita Vikas Hole
https://www.linkedin.com/in/ruchita-hole-1607323b6/ | ruchitahole09@gmail.com
