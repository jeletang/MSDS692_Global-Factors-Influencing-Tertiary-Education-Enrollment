# MSDS692_Global-Factors-Influencing-Tertiary-Education-Enrollment
## Overview
Over the last two decades, tertiary education enrollment, on a global scale, has more than doubled, from 18.4% in 1999 to 39.2% in 2019 (WorldBank, n.d.). The transition through education levels, however, have seen a different trend as the student population decreases at every further level. Enrollment rates are highest at the primary level, gets lower at the secondary level and is lowest at tertiary level. The intention of this project is to focus on country-specific factors and how they relate to tertiary education enrollment.

The dataset for this project was obtained from World Development Indicators as of 2019, published by World Bank, and in cases of missing data was supplemented by data from other trusted sources, listed below in the "Sources" section. The starting dataset comprised 266 observations (of which 217 were individual countries and 49 were aggregates based on World Bank classififcation) and 59 attributes. The focus of this project, tertiary education enrollment, was selected as the dependent target variable. By exploring relationships among factors including literacy rates, employment information, and access to utilities, we can not only discover how they affect tertiary education enrollment, but also learn areas to address in an effort to encourage enrollment.

To demonstrate correlated global factors, visualization was used, as well as regression modeling since the target is numeric.

## EDA and Modeling
The dataset contained data for individual countries as well as aggregates. Aggregates include regions, income levels, lending groups, demographic dividend groups and small states, as classified by World Bank. Keeping in mind that individual country data formed part of aggregate data, these two sections were made into separate datasets and analyzed as such. Columns and rows with missing data were dropped, since values to fill them were not readily available and imputing them could result in incorrect values (and therefore inaccurate modeling) given that the entire dataset comprised real-world data at a given time. For this same reason, most outliers were kept. Duplicate observations were dropped.

After generating a correlation matrix, features with least correlation to the target were dropped. Additionally, features that could have been just as dependent on, or influenced by, the target were dropped, including life expectancy and mortality. This reduced the aggregate dataset to 41 observations and 24 features, and the countries dataset to 178 observations and 19 features. 

Regression analysis was conducted using several different modeling techniques. Their results were evaluated using R-squared score, mean absolute error, mean squared error and root mean squared error. Their R-squared test scores are shown below:
| Technique  | Agg. (75/25) | Ctry. (80/20) |
| ------------- | ------------- | ------------- |
| Principal Component Regression  | 94% | 67% |
| Random Forest  | <b>97%</b>  | 75% |
| Linear  | 93%  | 69% |
| Decision Tree  | 94%  | 63% |
| K-Nearest Neighbors (KNN)8 | 95%  | <b>80%</b> |

On aggregate data, the Random Forest model performed best. On countries data, the KNN model outperformed the others, though it could be better.

## Summary/Conclusions
<img width="944" alt="tee_by_region_income_2019" src="machine learning/tee_by_region_income_2019.png">

Using the aggregate dataset, the North American and Europe & Central Asia regions had the highest tertiary education enrollment rates, while the Sub-Saharan African region had the lowest. Several global factors influence, and are influenced by, tertiary education enrollment. These include secondary school enrollment, access to utilities such as water and sanitation, literacy, adolescent fertility, and duration (years) of preprimary education, as determined by the Random Forest model tested on aggregate data. With the exception of adolescent fertility, the strongest influencing factors were positively correlated to the target.

<img width="643" alt="rf_influencing-factors" src="machine learning/rf_influencing-factors.png">

These results mean that secondary school enrollment (and completion) contributes positively to enrollment in higher education. With regard to water and sanitation access, these are basic health needs and it stands to reason that healthy students are better equipped to learn and apply knowledge. Preprimary education and literacy are fundamentals to any level of education, and both fuel engagement and continued learning, which culminates at the tertiary level. Adolescent fertility and tertiary education enrollment rates naturally move in opposite directions as they require different responsibilities and dedication of resources.

More could be learned about factors influencing tertiary education enrollment if features could be drilled down further into demographics such as age, sex, and income per capita. Since this data is collected over time, a time series analysis could be conducted to take into accounts impactful events such as natural disasters. Further exploration and evaluation of this data should continue, to address areas that most affect education in an effort to increase enrollment rates globally.

## Sources
 - World Bank
 - International Labour Organization
 - United States Agency for International Development
 - United Nations
 - Central Intelligency Agency
 - Our World in Data

## References
<i>Charts</i>. (n.d.). Our World in Data. <b>https://ourworldindata.org/charts</b>

<i>Guide to Country Comparisons</i>. (n.d.). The World Factbook - CIA. <b>https://www.cia.gov/the-world-factbook/references/guide-to-country-comparisons/</b>

<i>IDEA</i>. (n.d.). <b>https://idea.usaid.gov/cd</b>

ILO Department of Statistics. (n.d.). <i>Topics - ILOSTAT</i>. ILOSTAT. <b>https://ilostat.ilo.org/topics/</b>.

<i>Indicators</i>. (n.d.). World Bank Open Data. <b>https://data.worldbank.org/indicator/</b>.

<i>SDG 6 Data</i>. (n.d.). <b>https://www.sdg6data.org/en</b>
WorldBank. (n.d.). <i>School enrollment, tertiary (% gross)</i>. World Bank Gender Data Portal. <b>https://genderdata.worldbank.org/indicators/se-ter-enrr/?gender=total&view=trend</b>.

UN Data. (n.d.) <b>https://data.un.org/</b>
