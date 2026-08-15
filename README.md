Starwars Character Characterization and Demographics
================
Richie Peng

# Project Introduction

This side project is an exploratory data analysis based on R and the `starwars` dataset. The following analysis covers the complete data science workflow from **data exploration, data cleaning, descriptive statistics visualization, advanced data manipulation, to statistical inference and modeling (linear regression and logistic regression)**, examining Star Wars characters and metrics from multiple analytical perspectives.

### Key Findings & Takeaways

- **Data Exploration & Cleaning**: Successfully filtered multi-condition samples (e.g., older, non-black-haired characters) and engineered a binary feature for species (`Human` vs. `Non-human`), showing that human characters constitute the largest proportion in the Star Wars universe.
- **Advanced Data Manipulation**: Utilized `lapply` and `do.call` to unnest list-columns, automatically extracting the tallest character representation from each film (e.g., Chewbacca ranks as the tallest character across 4 films).
- **Modeling & Statistical Insights**:
  - **Outlier Diagnostics**: In the linear regression between mass and height, an extreme outlier (Jabba the Hutt, 1,358 kg) was identified as severely distorting model fit; after removing the outlier, mass demonstrated a highly significant positive predictive effect on height ($p < 0.001$).
  - **Multiple Regression & Control Variables**: When controlling for gender, each 1 kg increase in mass predicts an average height increase of approximately 1.05 cm, with masculine characters being significantly shorter on average than feminine characters at the same mass.
  - **Binary Probability Estimation**: Through logistic regression and `visreg` visualization, masculine characters exhibited a higher predicted probability of baldness (lack of hair) compared to feminine characters.

------------------------------------------------------------------------

# 1. Data Exploration

Prior to in-depth analysis, an initial exploration of the dataset is conducted to extract samples meeting specific criteria.

## Q1. Identifying Extreme Values and Conditional Means

**Find the name and `mass` of the lightest character in the `starwars` dataset; calculate the `mean` `mass` for characters with a `height` greater than 150 cm (excluding missing values `NA`).**

``` r
# 1. Find the name and mass of the lightest character
lightest_character <- starwars[which.min(starwars$mass), c("name", "mass")]
print("Lightest character:")
