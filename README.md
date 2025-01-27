# COVID-19 India Vaccination Insights Using Looker Visualization

## Introduction
This repository presents insights from the COVID-19 vaccination data of India, visualized using Looker. The dataset includes state-wise vaccination data, age group breakdowns, precautionary doses, and total vaccinations.

### Data Overview
The dataset provides comprehensive insights into the vaccination progress across India. This project includes visualizations on:
- **State-wise total vaccinations**
- **Age group-wise vaccination breakdown**
- **Proportion of precautionary doses**

---

## Code for Analysis

### Loading and Inspecting Data

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from IPython.display import Image, display

# Load Data
data = pd.read_csv('/path-to-your-data/covid19-india-statewise-vaccine-data/COVID-19 India Statewise Vaccine Data.csv')
data.head()
```

### Summarizing Total Vaccinations Across States

```python
# Summarize total vaccinations across states
total_vaccinations_by_state = data.groupby('State/UTs')['Total Vaccination Doses'].sum().sort_values(ascending=False)

# Plot the top 10 states with the highest total vaccinations
plt.figure(figsize=(10, 6))
sns.barplot(x=total_vaccinations_by_state.head(10).values, y=total_vaccinations_by_state.head(10).index, palette="viridis")
plt.title("Top 10 States by Total Vaccinations", fontsize=16)
plt.xlabel("Total Vaccination Doses", fontsize=12)
plt.ylabel("State/UT", fontsize=12)
plt.show()
```

### Age Group Analysis

```python
# Age Group Analysis
dose_1_15_18 = data['Dose 1 15-18'].sum()
dose_2_15_18 = data['Dose 2 15-18'].sum()
dose_1_12_14 = data['Dose 1 12-14'].sum()
dose_2_12_14 = data['Dose 2 12-14'].sum()

age_group_data = {
    "Age Group": ["15-18 Dose 1", "15-18 Dose 2", "12-14 Dose 1", "12-14 Dose 2"],
    "Vaccinations": [dose_1_15_18, dose_2_15_18, dose_1_12_14, dose_2_12_14]
}
age_group_df = pd.DataFrame(age_group_data)

plt.figure(figsize=(8, 5))
sns.barplot(data=age_group_df, x="Age Group", y="Vaccinations", palette="coolwarm")
plt.title("Vaccinations by Age Group", fontsize=16)
plt.xlabel("Age Group", fontsize=12)
plt.ylabel("Number of Vaccinations", fontsize=12)
plt.show()
```

### State-wise Vaccination Insights

```python
# Proportion of precautionary doses
precautionary_doses = data['Precaution 18-59'].sum()

plt.figure(figsize=(8, 8))
plt.pie([precautionary_doses, total_vaccinations_by_state.sum() - precautionary_doses], labels=["Precaution Doses", "Others"], autopct="%1.1f%%", colors=["#ff9999","#66b3ff"])
plt.title("Proportion of Precautionary Doses in Total Vaccinations", fontsize=16)
plt.show()
```

---

## Insights

### Key Findings

- **Uttar Pradesh** emerged as the leading state with the highest number of vaccinations.
- **Age-specific vaccination campaigns**, particularly for the **15-18 age group**, significantly impacted vaccination coverage.
- **Precautionary doses accounted for 7.2%** of total vaccinations, emphasizing proactive measures to safeguard public health.

These insights underline the importance of targeted vaccination strategies and the effectiveness of India's vaccination drive.

---

## Live Looker Dashboard

Explore the interactive Looker dashboard for real-time analysis and insights:

[Click to View Live Dashboard](https://your-looker-dashboard-link.com)

> **Note:** Ensure you have the necessary permissions to view the dashboard.

---

## Visualizations

### Screenshots of Google Site and Looker Dashboards

#### Google Site Screenshot
![Google Site](https://your-image-link.com/google-site-screenshot.png)

#### Looker Dashboard Screenshots

- **Dashboard 1**
  ![Looker Dashboard 1](https://your-image-link.com/looker-dashboard-1.png)

- **Dashboard 2**
  ![Looker Dashboard 2](https://your-image-link.com/looker-dashboard-2.png)

- **Dashboard 3**
  ![Looker Dashboard 3](https://your-image-link.com/looker-dashboard-3.png)

- **Dashboard 4**
  ![Looker Dashboard 4](https://your-image-link.com/looker-dashboard-4.png)

- **Dashboard 5**
  ![Looker Dashboard 5](https://your-image-link.com/looker-dashboard-5.png)

---

## Conclusion

The **Looker visualization** revealed critical insights from India's COVID-19 vaccination data. Key findings include:

- **Uttar Pradesh** emerged as the state with the highest number of vaccinations.
- **Age-specific vaccination campaigns** for the **15-18 age group** played a key role in improving vaccination coverage.
- **Precautionary doses** accounted for 7.2% of total vaccinations, showcasing the proactive efforts to protect public health.

These insights emphasize the significance of strategic vaccination campaigns and India's approach to combating COVID-19.

---
