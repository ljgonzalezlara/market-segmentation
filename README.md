# Market Segmentation Using KMeans Clustering

## Objective
This project applies KMeans clustering to ZIP code-level data in Lake County, IL to identify distinct market segments based on socioeconomic characteristics such as income, poverty, and population density. The insights support targeted business strategies, including localized marketing.

## Dataset
- [Lake County, IL Demographics](https://catalog.data.gov/dataset/demographics-0be32)
- [Features](#features)

## Methods
- Data Cleaning and Preprocessing
- Feature Scaling
- KMeans Clustering
- Elbow Method
- Segment Analysis with Visuals

## Key Findings
- Three market segments found based on median income and population density:
  - Mixed Income - High Density Area
  - Moderate Income - Medium Density Area
  - High Income - Medium Density Area
- Recommendations - Three ZIP codes best suited for marketing campaigns:
  - 60089 from Mixed Income - High Density Area
  - 60061 from Moderate Income - Medium Density Area
  - 60035 from High Income - Medium Density Area

Initially, three market segments were found when clustering was based solely on median income using Univarite Clustering. The cluster statistics below are sorted by the median income mean per cluster in ascending order, in USD, which helps illustrate the relationship between income level and socioeconomic indicators such as poverty and food stamp usage. Poverty and food stamp variables are the mean percentage per cluster.

### Cluster Counts

|   Income_Cluster |   Count |
|-----------------:|--------:|
|                0 |       6 |
|                1 |       9 |
|                2 |      12 |

### Demographic Characteristics by Cluster

|   Income_Cluster |   Med_Income |   Poverty |   Food_Stamp |
|-----------------:|-------------:|----------:|-------------:|
|                1 |      52845.4 |  15.4778  |     15.4467  |
|                2 |      85550.3 |   5.60833 |      5.62419 |
|                0 |     128537   |   4.5     |      2.06233 |

After identifying segments based on income alone, a second clustering approach incorporated both median income and poverty rates to gain a more nuanced view of socioeconomic conditions. Using Bivariate Clustering, the groups were then broken into four segments when poverty levels in percentages per ZIP code were added as the second feature, alongside median income. Note that the cluster statistics are ordered by median income mean per cluster in ascending order and poverty and food stamp features are percentage means.

### Cluster Counts

|   Income_Poverty_Cluster |   Count |
|-------------------------:|--------:|
|                        0 |       6 |
|                        1 |       8 |
|                        2 |      11 |
|                        3 |       2 |

### Demographic Characteristics by Cluster

|   Income_Poverty_Cluster | Cluster_Group_Name                 |   Med_Income |   Poverty |   Food_Stamp |
|-------------------------:|:-----------------------------------|-------------:|----------:|-------------:|
|                        3 | Low Income - High Poverty          |      36958   |  26.8     |     27.9425  |
|                        1 | Moderate Income - Moderate Poverty |      59702.6 |  12.025   |     11.333   |
|                        2 | Moderate Income - Low Poverty      |      86425.1 |   5.16364 |      5.45105 |
|                        0 | High Income - Low Poverty          |     128537   |   4.5     |      2.06233 |

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Income_Poverty.png?raw=true)

To improve upon a basic income-based categorization of ZIP code areas, we introduced population density as the second feature in our clustering model, alongside median income. This allowed us to account not only for how much income residents earn, but also for how concentrated or spread out those residents are. This is a factor that can significantly affect cost of living, infrastructure needs, and consumer behavior. This change reclassified various ZIP codes by once again segmenting the clusters into 3 groups. This shift reflects how a broader context, including space and crowding, can offer a more nuanced understanding of regional demographics. 

### Cluster Counts

|   Income_Pop_Density_Cluster |   Count |
|-----------------------------:|--------:|
|                            0 |       6 |
|                            1 |       6 |
|                            2 |      15 |

### Demographic Characteristics by Cluster

|   Income_Pop_Density_Cluster | Cluster_Group_Name               |   Med_Income |   Poverty |   Food_Stamp |
|-----------------------------:|:---------------------------------|-------------:|----------:|-------------:|
|                            1 | Mixed Income - High Density      |      58846.8 |   15.9333 |     14.7031  |
|                            2 | Moderate Income - Medium Density |      76608.8 |    7.4    |      7.88614 |
|                            0 | High Income - Medium Density     |     128537   |    4.5    |      2.06233 |

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Income_Density.png?raw=true)

This brought us to the final three market segments found, where the first cluster with mixed incomes contained the most variance. Here are some of the demographic information per segment.

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Age_Comp.png?raw=true)

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Ed_Comp.png?raw=true)

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Racial_Comp.png?raw=true)

We identified ZIP codes 60089, 60061, and 60035 as optimal targets for marketing campaigns based on their strong combination of median income and population density. These areas represent a strategic intersection of purchasing power and potential foot traffic, with median incomes ranging from approximately $91,000 to $115,000 and population densities between 2,400 and 5,000 people per square mile.

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Age_Comp_Final.png?raw=true)

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Ed_Comp_Final.png?raw=true)

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Racial_Comp_Final.png?raw=true)

![](https://github.com/ljgonzalezlara/market-segmentation/blob/main/images/Mixed_Final.png?raw=true)

The three ZIP codes—60089, 60061, and 60035—represent a highly educated demographic with similar age distributions. ZIP codes 60089 and 60061, part of the mixed-income and moderate-income tiers respectively, showed slightly more racial diversity, though all three areas remain predominantly white. These patterns suggest that marketing campaigns targeting these areas may achieve higher engagement rates. Further analysis could help identify other high-density areas that offer greater potential for outreach, particularly for social or educational services.

## Tools Used
- Python (pandas, scikit-learn, matplotlib, seaborn)
- Jupyter Notebook

---

## Features
- ZIP - ZIP codes within Lake County, Illinois.
- Total Population – Total population per ZIP code in Lake County.
- White – Individuals who are of Caucasian race. This is a percent.
- African American – Individuals who are of African American race. This is a percent.
- Asian – Individuals who are of Asian race. This is a percent.
- Hispanic – Individuals who are of Hispanic ethnicity. This is a percent. 
- Does not Speak English- Individuals who speak a language other than English in their household. This is a percent.
- Under 5 years of age – Individuals who are under 5 years of age. This is a percent.
- Under 18 years of age – Individuals who are under 18 years of age. This is a percent.
- 18-64 years of age – Individuals who are between 18 and 64 years of age. This is a percent.
- 65 years of age and older – Individuals who are 65 years of age or older. This is a percent.
- Male – Individuals who are male in gender. This is a percent.
- Female – Individuals who are female in gender. This is a percent.
- High School Degree – Individuals who have obtained a high school degree.  This is a percent.
- Associate Degree – Individuals who have obtained an associate degree. This is a percent.
- Bachelor’s Degree or Higher – Individuals who have obtained a bachelor’s degree or higher. This is a percent.
- Utilizes Food Stamps – Households receiving food stamps/ part of SNAP (Supplemental Nutrition Assistance Program). This is a percent. 
- Median Household Income - The income level earned by given households per ZIP code, where half of the homes in the area earn more and half earn less. This is a dollar amount.
- No High School – Individuals who have not obtained a high school degree. This is a percent.
- Poverty – Poverty refers to families and people whose income in the past 12 months is below the poverty level. This is a percent.
- Area - Area measured per ZIP code. This is a measurement in square feet.
- Length - Length measured per outer boundary of ZIP code. This is a measurement in feet.

Disclaimer:
This project was created for educational and practice purposes only. The analysis and results presented are based on simulated or publicly available data and should not be used to inform real-world business decisions without further validation.
