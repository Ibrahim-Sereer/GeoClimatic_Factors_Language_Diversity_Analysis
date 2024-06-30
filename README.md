# Data Analysis on Geographic and Climatic Factors Affecting Language Diversity

## Table of contents

- [Project overview](project-overview)
- 
### project overview 

This project analyzes the relationship between geographic/climatic factors and language diversity using data from Nettle (1998). The dataset includes 74 countries with variables such as the number of languages spoken, population size, area, and growing season length. The aim is to determine if longer growing seasons correlate with higher language diversity. By examining these variables and visualizing their relationships, the analysis seeks to uncover patterns and insights into how ecological conditions might influence linguistic diversity across regions. This project serves as a portfolio piece demonstrating skills in data manipulation, visualization, and statistical analysis.

### Tools

- R - Data analysis and visualization [download here] (https://www.r-project.org/)

### Data clealing/preperation 

Data Exploration Phase:

1. Displayed the first few rows of the dataset to get an initial look at the data.
2. Summarized the dataset to understand the distribution and basic statistics of each variable.
3. Checked the structure and types of variables in the dataset.

Variable Identification Phase:

1. Identified the categorical variables as country and continent.
2. Identified the continuous variables as langs, population, area, and growing.season.

Data Analysis Phase:

1. Summary Statistics:
   
- Calculated the total area, total population, and total number of languages across all countries.
- Counted the number of countries in each continent.
- Summarized the total number of languages and mean growing season per continent.
- Identified the countries with the highest number of languages.

2. Visualization:

- Created scatter plots to visualize the relationship between the number of languages and population.
- Faceted the scatter plots by continent to see the relationship within each continent.
- Filtered out countries with more than 250 languages to focus on the main trends and recreated the scatter plot.

New Variable Creation Phase:

1. Language Density:
   
- Created a new variable to represent the number of languages per million people.

2. Scatter Plot of Language Density and Growing Season:

- Created a scatter plot to visualize the relationship between language density (languages per million people) and the growing season, filtering out outliers.
- Added titles and labels to the plot.

3. Categorizing Growing Season:

- Created a new categorical variable indicating whether the growing season is longer than the median.
- Used a more informative label for the growing season category with values "long" and "short".

Statistical Analysis Phase:

1. Hypothesis Testing:
   
- Defined the null hypothesis: countries with long growing seasons do not have a higher language density than countries with short growing seasons.
- Defined the alternative hypothesis: countries with long growing seasons have a higher language density than countries with short growing seasons.

2. Confidence Intervals:

- Calculated the mean language density for countries with long and short growing seasons.
- Computed the 95% confidence intervals for the mean language density of both groups.

3. Conclusion:

- Determined that there is no significant difference in language density between countries with long and short growing seasons based on overlapping confidence intervals. This suggests that growing season length alone may not be a strong predictor of language diversity.

### Exploratory Data Analysis (EDA)

Total Aggregates:

- What is the total area of the countries in the dataset?
- What is the total population of the countries in the dataset?
- What is the total number of languages spoken in the countries in the dataset?

Continent-wise Distribution:

- How many countries are there in each continent?
- How many languages are spoken in each continent?
- What is the mean growing season for each continent?

Country-specific Insights:

- Which countries have the highest number of languages?

Relationship Exploration:

- What is the relationship between the number of languages and population size?
- How does the relationship between the number of languages and population size vary across different continents?
- What is the relationship between language density (languages per million people) and the growing season?
- Does a longer growing season correlate with a higher language density?
- Are countries with longer growing seasons associated with higher language diversity compared to countries with shorter growing seasons?
- How does the language density differ between countries with long and short growing seasons?
   
### Data analysis

```R
# Create a new variable for language density (languages per million people)
nettle_data <- nettle_data %>%
  mutate(langs_per_pop = langs / population)

# Create a scatter plot to visualize the relationship between language density and growing season
ggplot(nettle_data %>% filter(langs_per_pop <= 50), aes(x = growing.season, y = langs_per_pop)) +
  geom_point() +
  labs(title = "Language Density vs Growing Season",
       x = "Growing Season (months)",
       y = "Languages per Million People")
```

### Results/Findings

Total Aggregates:
- The total area of the countries in the dataset is 416.2 million square kilometers.
- The total population of the countries in the dataset is approximately 295 million people.
- The total number of languages spoken across these countries is 6640.

Continent-wise Distribution:
- Africa has the highest number of countries (37), followed by Asia (16), South America (12), North America (5), and Oceania (4).
- Africa also has the highest total number of languages (2513), followed by Asia (1977), Oceania (1273), South America (601), and North America (276).
- Oceania has the longest mean growing season (10.2 months), followed by South America (9.07 months), North America (7.99 months), Asia (6.39 months), and Africa (6.17 months).

Country-specific Insights:

- Papua New Guinea has the highest number of languages (862), followed by Indonesia (701), Nigeria (427), India (405), Cameroon (275), and Mexico (243).

Relationship Exploration:

- There is a weak positive relationship between the number of languages and population size, indicating that population size alone does not explain language diversity.
- When examined by continent, the relationship between the number of languages and population size varies, suggesting other factors are influencing language diversity.
- The relationship between language density (languages per million people) and the growing season appears weak, with no clear trend indicating that longer growing seasons significantly impact language density.
- Countries with longer growing seasons do not have a significantly higher language density compared to countries with shorter growing seasons, as indicated by overlapping confidence intervals.

These findings challenge the initial hypothesis that longer growing seasons might support greater language diversity, suggesting that other factors play a more significant role in determining language diversity across different regions.

### Recommendations

- Consider Additional Factors: Since the growing season alone does not significantly explain language diversity, future research should include other variables such as historical, cultural, and socio-economic factors to get a more comprehensive understanding of language diversity.
- Geospatial Analysis: Incorporate geospatial analysis to visualize and analyze the spatial distribution of languages and how they correlate with various geographic and climatic factors.
- Longitudinal Studies: Conduct longitudinal studies to understand how changes in climatic conditions over time affect language diversity and density.
- Data Collection: Improve data collection methods to include more detailed information on cultural practices, migration patterns, and historical events that might influence language diversity.

### Limitations

- Data Scope: The dataset includes only 74 countries, which may not represent the global diversity adequately. Some regions with significant linguistic diversity might be underrepresented.
- Variable Selection: The analysis primarily focused on geographic and climatic factors, potentially overlooking other crucial variables such as political, historical, and socio-economic factors that could influence language diversity.
- Data Quality: The dataset relies on secondary data from Nettle (1998), and there might be inconsistencies or inaccuracies in the reported values.
- Temporal Aspect: The dataset does not account for temporal changes. Linguistic diversity and growing seasons might have changed over time due to various factors, which this analysis does not capture.
- Statistical Methods: The use of simple statistical methods may not capture complex relationships between variables. More sophisticated methods might be necessary to uncover deeper insights.
- Generalization: The findings from this analysis may not be generalizable to all countries or regions, as the factors influencing language diversity can vary widely across different contexts.
- Cultural and Social Dimensions: The analysis does not account for the cultural and social dimensions of language use, which can significantly impact language diversity and density.

### References

Dataset Source:

- Provided in STAB23H3 - Statistics for the Life and Social Sciences, University of Toronto Scarborough (UTSC), taught by Emily Clare.

Learning Material:

- STAB23H3 - Statistics for the Life and Social Sciences, University of Toronto Scarborough (UTSC)
- Instructor: Emily Clare
- Contact: (e.clare@mail.utoronto.ca)

R Documentation:

- R Core Team (2023). R: A language and environment for statistical computing. R Foundation for Statistical Computing, Vienna, Austria. URL (https://www.R-project.org/)

Additional Resources:

- Winter, B. (2020). Statistics for Linguists: An Introduction Using R. Routledge.
