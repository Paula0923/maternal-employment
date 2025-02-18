# Comparison of Maternal Employment and Related Indicators in EU Countries ![woman_eu](images/woman_eu.png)

![mother-951187_1280](images/mama.jpg)

## Overview
In this project, I analyse various influence factors on maternal employment in the member countries of the European Union. The data was gathered from OECD Family Database and Eurostat and includes the EU-27. Using Exploratory Data Analysis, Inferential Statistics and Regression Models, my goal is to find out why maternal employment rates are different in the countries and which factors might influence this.

## Main Interest
My main goal is to find out **what influences the level of maternal employment**, so if women who have at least one child are part of the labour market. I particularly want to find out to what extent the length of **paternal parental leave** and the proportion of **men working part-time** have an influence. but also whether countries with **higher public spending on families** have a higher employment rate of mothers, what role the **gender pay gap** plays and the number of **women in management positions**.

## Dataset
The data set was compiled from the [**OECD Family Database**](https://www.oecd.org/en/data/datasets/oecd-family-database.html) and [**Eurostat Database**](https://ec.europa.eu/eurostat/web/main/data/database). After extracting the data (~15 excel tables), I transformed the tables using excel so that they would all have the following characteristics: column "country" in common, structure of a pandas DataFrame (2D tables) and only content relevant for the analysis. In the **data folder** in this repository, you can find an excel file [**overview_data**](data/overview_data.xlsx) in which all transformed tables and sheets are linked to the original source. The dataset then imported into VSCode had the following characteristics:
- ~29 columns with information on ~60 countries
- No time series, the data is always from either the last available year or the last year with the most complete data possible (this usually means 2021-2023 but for some (few) columns 2015 and others 2024).
- Columns i.e. contain the following information: GDP, unemployment, maternal employment, part-time rates, gender pay gap, leave policies etc.

## Approach
In order to have a comprehensive dataset, I limited the number of countries to only **members of the European Union** because the data was most complete. I had to exclude Slovakia and Czech Republic from the analysis because the data for them had a missing values rate of over 60%.
After cleaning the data, I created some new columns using feature engineering. In this case, I used logarithmic transformation, scale normalization and categorization to have new, comparable columns on the education levels of women and the spending on family benefits.
I then formulated hypotheses and analysed them using EDA methods. In the event that this gave me indications of the possible confirmation of a hypothesis, I then tested the respective hypothesis with inferential statistics: primarily with t-tests, ANOVA and OLS regression.
Finally, I included all indicators in an OLS regression model and improved this model step by step until I found a set of variables that explained a good part of maternal employment.

## Key Findings
| Hypothese    | EDA Finding | Inferential review     |
|:---------|:-------:|:----------:|
| H1: Countries with higher public spending on family benefits have a higher maternal employment rate.    | ❌    |    |
| H2: Mothers in partnerships have a higher employment rate than single mothers. This difference is smaller in countries with higher spending on family benefits.     | ✅    | ❌  |
| H3: Countries with longer fully paid parental leave for fathers have a higher maternal employment rate. | ✅     | ❌  |
| H4: The higher the education level of women in a country, the higher the maternal employment rate.    | ✅     | ✅ (20.6%)   |
| H5: Countries with a higher proportion of female managers have higher maternal employment rates.     | ❌    |   |
| H6: In countries where more men work part-time, maternal employment rates are higher. | ✅     | ❌  |
| H7: In countries with a lower gender pay-gap, maternal employment rates are higher. | ❌    |   |




## Repository Content
- First of all, this repo contains the code I used to analyse my dataset: a notebook on eda (which also includes cleaning and feature engineering) (**eda-maternal-employment**) and a different one on hypothesis testing and regression analysis (**inferential-maternal-employment**). Also, you can find the **requirements for the code** here.
- In the **data folder**, you can find the **original data** with excel files downloaded from OECD and Eurostat, as well as the **edited data** which I edited structurally, so that I could import and merge it using python.
- Additionally, there is a odf with the **presentation** on my findings and also challenges and limitations of the project. You can also find the presentation [**here**]("https://").
**NOCH URL EINFÜGEN**

## About the Author
Paula Boks

Political Scientist with a love of numbers, currently in an additional qualification program as data analyst.

![book](images/book.jpg)