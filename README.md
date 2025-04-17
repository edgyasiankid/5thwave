# Survival Score Visualization: The Others Invasion Scenario

This project explores the survivability of countries in the event of a fictional alien invasion — inspired by *The Others* from **The 5th Wave**. Using demographic-style data, I analyze how well different populations might resist, survive, and rebuild based on education, income, and age characteristics.

I calculate **z-scores** to standardize each factor, weight them according to post-invasion survival importance, and visualize the results using an **interactive stacked bar chart**.

---

## What This Project Does

- Processes demographic data for each country
- Calculates z-score–based contributions for:
  - **Education level**
  - **Income distribution**
  - **Age distribution**
- Computes a **Survival Score** based on weighted components
- Visualizes each country’s survival profile as an **interactive stacked bar chart**

[View Results](RESULTS.md)

---

## Scoring Logic

### Why Z-Scores?

A **z-score** tells us how a country compares to the global average:
- **Positive z-score** → better than average
- **Negative z-score** → worse than average
- The higher the magnitude, the more extreme the difference

### Education Score

Calculated based on education level proportions:

**Education Score** = (2 × Graduate z-score)

+ (1 × Undergraduate z-score)

- (0.5 × High School z-score)

- (-1 × Elementary z-score)


Higher education levels imply better preparedness for organizing resistance, innovating, and rebuilding after societal collapse.

### Age Score

Age scores are derived from the z-score of the average age in each country, but **inverted** so that younger populations receive a higher score:

**Age Score** = -1 × z-score(mean age)

Younger populations are favored in this scenario for their agility, adaptability, and resilience — critical traits in surviving and rebuilding after a global crisis.

### Income Score

Income scores are based on the ratio of individuals earning more than \$50K to those earning less than or equal to \$50K:

**Income Score** = z-score[(# of people >50K) / (# of people <=50K)]

A higher income ratio suggests better infrastructure, access to resources, and economic stability — factors that could modestly improve survivability. However, income is weighted less compared to education and age, given the collapse of conventional financial systems in this scenario.

## Sample Size

Sample size was incorporated into the final **Survival Score** by applying a logarithmic weight during score computation. While the z-scores for education, income, and age were calculated based on standardized values across countries, the **sample size** for each country was used to adjust the **impact or confidence** of those scores. Countries who had less than 30 data points were excluded from this analysis.

### Why Weight by Sample Size?

Countries with larger sample sizes (e.g., United States) offer more reliable demographic trends, while smaller sample sizes may skew the z-scores due to statistical noise or anomalies. To balance this:

- A **logarithmic function** (`log(sample_size)`) was applied to moderately scale the impact of survival scores.
- This prevents countries with extremely large samples from dominating the rankings purely due to volume.
- It also avoids completely disregarding smaller-sample countries, instead giving them proportional influence.

### Formula Adjustment

The raw weighted score was scaled like this:

**Adjusted Survival Score** = Raw Score × log(sample_size)


This preserves the **direction and weighting of each component** (education, income, age), while proportionally boosting the **confidence** in scores derived from more substantial data.

This technique helps ensure that the final rankings are statistically sound and not overly biased by underrepresented countries or sampling inconsistencies.

---

### Technologies Used
**KNIME** – For data processing, aggregation, and z-score calculation

**Python** – For scripting and plotting

**Pandas** – For CSV data handling

**Plotly** – For interactive chart visualization

[Original Dataset on Kaggle](https://www.kaggle.com/datasets/mastmustu/income)

---

### Running Program in Colab
1. Open .ipynb file in Colab
2. Download survival-scores.csv file
3. Import csv file in Colab

