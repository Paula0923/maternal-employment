# EU Comparison of Maternal Employment and Related Indicators

<img src="images/mama.jpg" alt="Mother and Child" width="400"/>  <img src="images/mama2.png" alt="Mother and Child" width="400"/>

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
1. In order to have a comprehensive dataset, I limited the number of countries to only **members of the European Union** because the data was most complete. I had to exclude Slovakia and Czech Republic from the analysis because the data for them had a missing values rate of over 60%.
2. After cleaning the data, I created some **new columns using feature engineering**. In this case, I used **logarithmic transformation, scale normalization and categorization** to have new, comparable columns on the **education levels of women** and the **spending on family benefits**.
3. I then formulated **hypotheses** and analysed them using **EDA methods**. In the event that this gave me indications of the possible confirmation of a hypothesis, I then tested the respective **hypothesis with inferential statistics**: primarily with t-tests, ANOVA and OLS regression.
4. Finally, I included all indicators in an **OLS regression model** and improved this model step by step until I found a set of variables that explained a good part of maternal employment.

## 🟠 **Key Findings: Hypotheses**
| Hypothesis    | EDA Finding | Inferential review     |
|:---------|:-------:|:----------:|
| H1: Countries with higher public **spending on family benefits** have a higher maternal employment rate.    | ❌    |    |
| H2: Mothers in **partnerships** have a higher employment rate than **single mothers**. This difference is smaller in countries with higher spending on family benefits.     | ✅    | ❌  |
| H3: Countries with longer fully paid **parental leave for fathers** have a higher maternal employment rate. | ✅     | ❌  |
| H4: The higher the **education level of women** in a country, the higher the maternal employment rate.    | ✅     | ✅  |
| H5: Countries with a higher proportion of **female managers** have higher maternal employment rates.     | ❌    |   |
| H6: In countries where more **men work part-time**, maternal employment rates are higher. | ✅     | ❌  |
| H7: In countries with a lower **gender pay gap**, maternal employment rates are higher. | ❌    |   |

## 🟠 **Key Findings: OLS Regression**
Many of the predictors do not have a linear relationship with the target, I therefore excluded them from the regression model in the end. After several steps to improve the model, three predictors were found to be very interesting:
**Unemployment**, the **education level of women** and the length of paid **leave for fathers**.

These three predictors together explain **46.3 %** (R² Adjusted: 38.6 %) of the maternal employment rate with the **individual impacts** being as follows (sorted by importance):
| Predictor                      | Unit             | Effect on Mat. Emp. | In std |
|--------------------------------|:---------------|:------------------|:------:|
| Fully Paid Leave for Fathers   | 🟢⬆️ by 1 week   | 🟢⬆️ by 0.8 %       | +3.5   |
| Education Level Women          | 🟢⬆️ by 1 point[^1] | 🟢⬆️ by 14.3 %      | +3.4   |
| Unemployment                   | 🟢⬆️ by 1 %       | 🔴⬇️ by 1.2 %       | -2.6   |

## 🟠 **Highlighting the Most Interesting Results**
1. If a country wants to increase maternal employment, there are several approaches for the effectiveness of which indications were found here:
    - An **extension of paternity leave** could improve maternal employment rates greatly. Also, in many countries, there is a lot of room for improvement regarding this.
    - **Raising the educational level of women** also is a great influence factor, most likely because this leads to better paid jobs (=more possibilities regarding child care) and more job security.
2. For countries struggling with a high maternal age at first birth (and with a low fertility, as these two correlate moderately):
    - There is a **great impact of the length of paid maternal leave on the age of first-time mothers**: An OLS regression showed that an extension of one week could lower the mother's age at first child by approx. two weeks.

## More on This Project
In the code and in the presentation, you can find many analyses and visualizations regarding the comparison of the countries. I.e. the fertility rate, age of mothers, gender pay gap, part-time rates etc. per country and in comparison to the others.

## Repository Content
- First of all, this repo contains the code I used to analyse my dataset: a notebook on eda (which also includes cleaning and feature engineering) (**eda-maternal-employment**) and a different one on hypothesis testing and regression analysis (**inferential-maternal-employment**). Also, you can find the **requirements for the code** here.
- In the **data folder**, you can find the **original data** with excel files downloaded from OECD and Eurostat, as well as the **edited data** which I edited structurally, so that I could import and merge it using python.
- Additionally, there is a odf with the **presentation** on my findings and also challenges and limitations of the project. You can also find the presentation [**here**]("https://www.canva.com/design/DAGfKMQn6C4/5c0Y3Y31uIcPZIidA-mW7A/edit?utm_content=DAGfKMQn6C4&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton").

## About the Author
Paula Boks, based in Riga and Berlin: **Political Scientist** with a love of numbers, currently in an additional qualification program as **data analyst**.

![hands-20333_1280](images/hands.jpg)

[^1]: The education level for women was created based on three columns with the rates on women with high/med/low education level. It is an artificial and standardized score from 0-1, so an increase of 1 % would i.e. mean that ~30 % of women in Italy (lowest score) move from a low education to a high education, so the change would be immense.