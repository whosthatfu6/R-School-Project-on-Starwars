### Starwars Character Characterization and Demographics
Richie Peng

### Project Introduction
This Side Project is a data analysis side project based on R and the `starwars` dataset. The following analysis covers the entire pipeline from **data exploration, data cleaning, descriptive statistics visualization, advanced data manipulation, to statistical inference and modeling (linear regression and logistic regression)**, approaching and analyzing Starwars characters and data from various angles.

##### Key Findings & Takeaways
*   **Data Exploration & Cleaning**: Successfully filtered samples under multiple conditions (e.g., elderly, non-black-haired characters), and performed binary feature engineering on the complex and diverse species structure (Human vs. Non-human), discovering that human characters account for the highest proportion in the Starwars universe.
*   **Advanced Data Manipulation**: Leveraged `lapply` and `do.call` to deconstruct list-columns, automatically extracting the tallest representative for each film (e.g., Chewbacca was identified as the tallest in 4 of the films).
*   **Modeling & Statistical Insights**:
    *   **Outlier Diagnosis**: In the linear regression of mass against height, an outlier (Jabba the Hutt, 1,358 kg) was identified as severely interfering with model fit; after excluding this outlier, mass demonstrated a highly significant positive predictive power on height ($p < 0.001$).
    *   **Multiple Regression & Control Variables**: When controlling for gender, each 1 kg increase in mass predicted an average increase in height of approximately 1.05 cm, and male characters had a significantly lower average height than female characters at the same mass.
    *   **Binary Probability Estimation**: Through Logistic Regression and `visreg` visualization, male characters demonstrated a significantly higher predicted probability of being bald (no hair) compared to female characters.

--------------------------------------------------------------------------------

### 1. Data Exploration
Before diving deep into the analysis, we first conduct a preliminary exploration of the dataset to extract samples under specific conditions.

#### Q1. Finding Extreme Values and Conditional Mean
**In the `starwars` dataset, find the name and mass value of the character with the lightest mass; and calculate the mean mass for characters with a height greater than 150 cm (excluding missing values NA).**

--------------------------------------------------------------------------------

#### Q2. Target Group Selection Under Multiple Conditions
**Filter out the specific character group with a `birth_year` greater than 50 years, a `mass` greater than 45 kg, and hair color that is "not" black, and export a data.frame containing only their name, birth year, mass, and hair color.**

| name | birth_year | mass | hair_color |
| ------ | ------ | ------ | ------ |
| Owen Lars | 52 | 120 | brown, grey |
| Obi-Wan Kenobi | 57 | 77 | auburn, white |
| Chewbacca | 200 | 112 | brown |
| Palpatine | 82 | 75 | grey |
| Bossk | 53 | 113 | none |
| Qui-Gon Jinn | 92 | 89 | brown |
| Jar Jar Binks | 52 | 66 | none |
| Darth Maul | 54 | 80 | none |
| Mace Windu | 72 | 84 | none |
| Ki-Adi-Mundi | 92 | 82 | white |
| Dooku | 102 | 80 | white |

List of characters matching the filtering criteria.

--------------------------------------------------------------------------------

### 2. Data Cleaning & Feature Engineering
Real-world data often contains missing values and complex categories; in this stage, we perform column merging and feature transformations.

#### Q3. Merging Species and Labeling Film Periods
**1. Perform feature engineering to create binary variables from the `species` column: if a character is human, classify them as "Human"; all other non-human species (including NA) are classified as "Non-human".**
**2. Create a new column `early_films`: mark whether the character appeared in the first three classic films "A New Hope" or "The Empire Strikes Back".**

--------------------------------------------------------------------------------

### 3. Descriptive Visualization
Present the feature engineering and cleaned data using plots to observe the distribution relationships between variables.

#### Q4. Plotting the Population Distribution of Each Species
**Calculate the occurrence count of each species and plot a bar chart. The bars must be sorted from largest to smallest, the actual count must be labeled on top of each bar, and the X-axis labels should be rotated 45 degrees to prevent text overlapping.**

--------------------------------------------------------------------------------

#### Q5. Parallel Distribution of Gender and Hair Color
**Explore the differences in occurrence counts across different hair colors for each gender (masculine vs. feminine), and present them using a grouped bar chart (dodge).**

--------------------------------------------------------------------------------

### 4. Advanced Data Manipulation
Focus primarily on how to deconstruct data with complex structures (such as list columns) and perform automated integration and analysis.

#### Q6. Automated Retrieval of the Tallest Height Representative in Each Starwars Film
**Since the `films` column has a complex list structure in the data.frame, design an automated integration process (avoiding manual step-by-step filtering) using `lapply`, `do.call`, and `rbind` to extract the name and height of the tallest character in each film, and produce a sorted data.frame and plot.**

| Film | Height | Name |
| ------ | ------ | ------ |
| A New Hope | 228 | Chewbacca |
| Attack of the Clones | 229 | Lama Su |
| Return of the Jedi | 228 | Chewbacca |
| Revenge of the Sith | 234 | Tarfful |
| The Empire Strikes Back | 228 | Chewbacca |
| The Force Awakens | 228 | Chewbacca |
| The Phantom Menace | 264 | Yarael Poof |

Tallest character representative in each Starwars film.

--------------------------------------------------------------------------------

### 5. Statistical Inference & Modeling
Establish regression models to validate relationships between variables and perform predictions.

#### Q7. Significance Analysis of Gender Differences on Height
**Establish a linear regression model to test whether there is a statistically significant difference in height between different genders (masculine vs. feminine), and interpret the p-value in the model analysis report.**

--------------------------------------------------------------------------------

#### Q8. Linear Relationship of Mass and Height and Outlier Impact Assessment
**Establish a linear regression model of mass on height, identify the outlier (e.g., Jabba the Hutt) that affects the model's significance, and evaluate the dramatic changes in the model's predictive power and significance (p-value and R-squared) before and after excluding the outlier.**

--------------------------------------------------------------------------------

#### Q9. Relationship Estimation Under Control Variables
**Establish a multiple regression model to assess the independent explanatory power of mass on height while controlling for the effect of the gender variable, and interpret the predicted change in height for each 1 kg increase in mass.**

--------------------------------------------------------------------------------

#### Q10. Probability Estimation of Physiological Characteristics by Gender
**When the dependent variable is a binary variable (e.g., whether bald `IsBald`), establish a logistic regression model to analyze the effect of gender on the probability of being bald, and use `visreg` to plot the predicted probability curves while controlling other conditions.**
