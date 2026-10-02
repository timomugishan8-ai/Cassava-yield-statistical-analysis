# Cassava Yield Statistical Analysis

## Overview

This project presents a statistical analysis of cassava yield data using **R and R Markdown**. The analysis investigates relationships between agricultural variables and cassava productivity, with particular focus on:

* The relationship between total tubers and total weight per hectare
* Differences in yield between conventional and minimum tillage
* The relationship between tillage method and fertilizer treatment
* Differences in cassava yield across fertilizer treatments

The project demonstrates a complete statistical analysis workflow, from data inspection and cleaning to exploratory visualization, hypothesis testing, interpretation, and practical recommendations.

---

## Research Questions

The analysis addresses three main questions:

1. **Is there a relationship between total tubers per hectare and total weight per hectare?**
2. **Does tillage method affect cassava yield?**
3. **Does fertilizer treatment affect cassava yield?**

The analysis also examines whether fertilizer treatment and tillage method are statistically associated.

---

## Dataset Preparation

The dataset was imported from Excel and prepared for analysis using R.

The preprocessing workflow included:

* Inspecting the structure and dimensions of the dataset
* Cleaning variable names using `janitor`
* Converting categorical variables to factors
* Assessing missing values
* Checking for duplicate observations
* Examining variable distributions
* Detecting potential outliers
* Applying winsorization to numeric variables

### Data Quality Findings

The dataset contained:

* **No missing values**
* **No duplicate observations**

Several numeric yield variables contained observations beyond the 1.5 × IQR boxplot boundaries. Because these observations could represent genuine agricultural variation rather than data-entry errors, winsorization was used instead of deleting observations.

---

## Exploratory Data Analysis

The analysis used several visualization techniques to understand the dataset:

* Histograms for continuous variables
* Bar charts for categorical variables
* Boxplots for identifying potential outliers and comparing groups
* Scatterplots for examining relationships between continuous variables

The yield variables showed noticeable variability and departures from normality, which informed the choice of non-parametric statistical tests.

---

## Statistical Methods

### 1. Continuous vs Continuous

The relationship between:

* `total_tuberper_hectare`
* `total_weightperhectare`

was examined using a scatterplot and Spearman's rank correlation.

Because the variables did not satisfy the normality assumption, Spearman correlation was used.

**Result:**

> Spearman's ρ ≈ 0.649, p < 0.001

This indicates a statistically significant, moderate-to-strong positive monotonic relationship between total tubers per hectare and total weight per hectare.

In practical terms, fields with higher tuber counts generally tended to have higher total cassava weight.

---

### 2. Continuous vs Categorical

Cassava yield was compared across the two tillage methods:

* Conventional (`conv`)
* Minimum (`minimum`)

Boxplots were used to compare the distributions, followed by normality testing and the Mann–Whitney U test.

For total weight per hectare:

> p ≈ 0.484

For the final tillage comparison of total tubers per hectare:

> p ≈ 0.196

These results do not provide evidence of a statistically significant difference in cassava yield between conventional and minimum tillage in this dataset.

---

### 3. Categorical vs Categorical

The relationship between:

* `tillage`
* `fer_t`

was examined using stacked and grouped bar charts.

A Chi-square test of independence was then performed.

**Result:**

> χ² test p = 1.00

The result does not provide evidence of a statistically significant association between tillage method and fertilizer treatment in the dataset.

---

## Fertilizer Treatment and Yield

The analysis also examined whether fertilizer treatment was associated with differences in cassava yield.

Boxplots were used to compare yield distributions across fertilizer treatment groups. Because normality was violated in a number of groups, the Kruskal–Wallis test was used.

For **total weight per hectare**:

> Kruskal–Wallis p ≈ 0.041

This indicates a statistically significant difference in total weight per hectare across the fertilizer treatment groups.

The analysis therefore suggests that fertilizer treatment is an important factor to investigate when examining differences in cassava productivity within this dataset.

---

## Key Findings

| Analysis                               |   Statistical result | Interpretation                           |
| -------------------------------------- | -------------------: | ---------------------------------------- |
| Tubers/ha vs Weight/ha                 | ρ ≈ 0.649, p < 0.001 | Significant positive relationship        |
| Weight/ha by tillage                   |            p ≈ 0.484 | No significant difference                |
| Tuber/ha by tillage                    |            p ≈ 0.196 | No significant difference                |
| Tillage × Fertilizer                   |          χ² p = 1.00 | No significant association               |
| Weight/ha across fertilizer treatments |         KW p ≈ 0.041 | Significant difference across treatments |

---

## Practical Recommendations

Based on the statistical evidence from this dataset:

1. **Pay attention to fertilizer treatment when evaluating cassava productivity**, since statistically significant differences in total weight per hectare were observed across fertilizer groups.

2. **Support practices that increase tuber formation**, since total tubers per hectare showed a strong positive relationship with total weight per hectare.

3. **Do not select conventional or minimum tillage solely on expected yield differences from this analysis**, since the observed differences were not statistically significant.

4. For a stronger agricultural recommendation, future analysis could incorporate additional variables such as soil characteristics, rainfall, location, season, fertilizer dosage, and other agronomic factors.

---

## Tools & Technologies

* **R**
* **RStudio**
* **R Markdown**
* **tidyverse**
* **readxl**
* **dplyr**
* **ggplot2**
* **skimr**
* **janitor**
* **GGally**
* **rstatix**
* **car**
* **patchwork**

---

## Project Structure

```text
cassava-yield-statistical-analysis/
│
├── data/
│   └── README.md
│
├── R/
│   └── Cassava_Yield_Data_Analysis.Rmd
│
├── output/
│   ├── Cassava_Yield_Data_Analysis.html
│   └── figures/
│
├── README.md
└── LICENSE
```

---

## Reproducibility

To reproduce the analysis:

1. Install **R** and **RStudio**.
2. Install the required R packages.
3. Place the dataset in the appropriate `data/` directory.
4. Open the R Markdown file.
5. Update the dataset path if necessary.
6. Knit the document to HTML or another supported output format.

---

## Author

**Timothy Mugisha**

Data Science & Analytics Student
Uganda Christian University

Interested in Data Science, Machine Learning, Business Intelligence, and Statistical Analysis.

---

## Academic Context

This project was completed as part of coursework in **Big Data Analytics and Technologies** at Uganda Christian University as a collaborative analysis by Group 3.

The repository presents the work in a portfolio-oriented format, emphasizing the analytical workflow, statistical methodology, interpretation, and practical insights.
