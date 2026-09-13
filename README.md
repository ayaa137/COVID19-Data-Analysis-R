# 🦠 COVID-19 Data Analysis in R

This project investigates how reported COVID-19 cases and deaths evolved during the early pandemic and how country-level mortality patterns relate to demographic, health, and socioeconomic characteristics.

The analysis combines daily COVID-19 data from the **World Health Organization (WHO)** with country-level indicators from the **World Bank Development Indicators (WDI)**. Germany is used as the main time-series case study, followed by European and global cross-country analyses.

## 🔍 Research Question

**How did COVID-19 evolve across countries during the early pandemic, and how were pandemic outcomes related to demographic, health, and socioeconomic characteristics?**

The analysis examines:

- COVID-19 case and death trends
- First-wave dynamics in Germany
- European mortality differences
- Case-to-death time delays
- Epidemic turning points
- Population and demographic structure
- GDP per capita
- Life expectancy
- Physicians per 1,000 people
- Population density
- Principal Component Analysis
- Cross-country mortality patterns

## 📊 Project Overview

The project includes:

- Data quality assessment and preprocessing
- COVID-19 time-series analysis
- 7-day moving-average smoothing
- Germany first-wave analysis
- European mortality comparison
- Case-to-death lag optimization
- First-wave turning-point detection
- World Development Indicators analysis
- Correlation analysis
- Principal Component Analysis
- Cross-country mortality regression
- Exponential growth modeling
- Cross-country lag and scale analysis
- Model diagnostics
- Limitations and interpretation

## 📦 Datasets

The project combines two datasets.

### WHO COVID-19 Data

The COVID-19 dataset contains:

- **237,474 daily observations**
- **237 countries**
- Data from **January 3, 2020 to September 30, 2022**
- Daily reported COVID-19 cases
- Daily reported COVID-19 deaths

**Source:** World Health Organization

[WHO COVID-19 Data](https://data.who.int/dashboards/covid19/data)

### World Development Indicators

The socioeconomic dataset contains information for **217 countries** and includes indicators such as:

- Population
- Population aged 65+
- Urban population
- Population density
- Physicians per 1,000 people
- Life expectancy
- GDP per capita

**Source:** World Bank — World Development Indicators

[World Development Indicators](https://databank.worldbank.org/source/world-development-indicators)

After country-name harmonization, **200 of the 237 WHO country series** could be matched to a World Bank population value for population-normalized analyses.

## 📈 Main Results

| Analysis | Result |
| --- | --- |
| Germany first-wave case-to-death lag | **4 days** |
| First-wave lag scale | **0.055** |
| First-wave lag RMSE | **19.5 daily deaths** |
| Germany early daily case growth | **22.0%** |
| Approximate early doubling time | **3.1 days** |
| PCA — PC1 variance explained | **63.0%** |
| PCA — PC2 variance explained | **17.3%** |
| PCA — PC1 + PC2 | **80.3%** |
| Mortality regression countries | **184** |
| Mortality regression adjusted R² | **0.560** |
| Cross-country lag analysis | **84 countries** |
| Median cross-country lag | **4 days** |

## 🇩🇪 Germany First-Wave Analysis

Germany is used as the main time-series case study.

The first wave accelerated rapidly during March 2020 before reaching its smoothed case peak in early April.

Important estimated turning points include:

- **Fastest increase:** March 20, 2020
- **Smoothed case peak:** April 4, 2020
- **Beginning of sustained decline:** approximately April 5, 2020

A 7-day moving average is used to reduce reporting noise and weekly reporting effects.

## ⏱️ Cases-to-Deaths Lag

A grid-search approach was used to estimate the time shift and scale that best align reported COVID-19 cases with later reported deaths.

For Germany's first wave:

- **Best lag:** 4 days
- **Estimated scale:** 0.055
- **RMSE:** approximately 19.5 daily deaths

The scale should not be interpreted as an infection fatality rate because it is based on **reported cases**, not all infections.

The relationship also changes substantially across different stages of the pandemic, reflecting changes in testing, vaccination, variants, clinical treatment, demographics, and reporting.

## 🌍 European Comparison

Germany was compared with:

- France
- Italy
- United Kingdom

Mortality was normalized by population using cumulative reported deaths per 100,000 people.

By the end of June 2020, Italy, France, and the United Kingdom had experienced substantially higher reported mortality per capita than Germany.

The comparison describes observed reporting outcomes and should not be interpreted as evidence that any individual policy or structural factor caused the differences.

## 🔗 Correlation Analysis

The World Development Indicators reveal strong relationships among several country characteristics.

Some of the strongest correlations include:

- GDP per capita and life expectancy: **0.84**
- GDP per capita and physicians per 1,000: **0.76**
- GDP per capita and population aged 65+: **0.72**
- GDP per capita and urban population: **0.69**

These relationships show that income, longevity, healthcare capacity, urbanization, and demographic structure are strongly interconnected across countries.

## 📉 Principal Component Analysis

Principal Component Analysis was used to summarize several correlated socioeconomic indicators.

The PCA used **193 complete country observations**.

The first components explain:

- **PC1:** 63.0%
- **PC2:** 17.3%
- **PC3:** 10.1%
- **PC4:** 4.3%

Together, **PC1 and PC2 explain 80.3% of the variation** in the selected indicators.

The strongest contributors to PC1 include:

- GDP per capita
- Life expectancy
- Physicians per 1,000
- Population aged 65+
- Urban population

PC2 is dominated more strongly by population density.

## 📊 COVID-19 Mortality Regression

A cross-country regression model was used to examine whether broad structural indicators are associated with COVID-19 mortality.

The final model uses **184 countries** and models log deaths per 100,000 population.

| Predictor | Estimate | p-value |
| --- | ---: | ---: |
| Log10 GDP per capita | 1.392 | < 0.001 |
| Population aged 65+ (%) | 0.070 | < 0.001 |
| Physicians per 1,000 | 0.074 | 0.449 |

The model achieves an **adjusted R² of 0.560**, meaning that approximately 56% of the variation in log deaths per 100,000 among complete observations is captured by the included predictors.

Life expectancy was excluded from the final model because of its strong correlation with income and age structure.

The model is descriptive and observational. The results should **not be interpreted as causal relationships**.

## 📈 Exponential Growth

Germany's early March 2020 case growth was approximately exponential.

A log-linear model estimates:

- **Daily reported case growth:** approximately 22.0%
- **Approximate doubling time:** 3.1 days

This describes the rapid early expansion of reported cases before behavioral changes, testing changes, public-health measures, and other factors altered the trajectory.

## 🌐 Cross-Country Lag Analysis

The case-to-death lag method was extended across countries with sufficient first-wave case and death data.

After data-quality filtering:

- **84 countries** were included
- The **median estimated lag was 4 days**
- Estimated scales varied substantially across countries

Twenty-five countries reached the lower search boundary of zero days. When a zero-day lag was disallowed, the median RMSE increase for these countries was only **1.6%**, suggesting that many of these boundary estimates represent weakly identified or relatively flat fits rather than strong evidence of same-day epidemiological timing.

The large variation in estimated scales is consistent with differences in testing, reporting, demographics, case composition, and health-system pressure across countries.

## 💡 Key Findings

- Germany's first COVID-19 wave accelerated rapidly during March 2020 and peaked in early April.
- Reported deaths followed the overall first-wave case pattern with an estimated optimized lag of **4 days**.
- Early German reported cases grew by approximately **22% per day**, corresponding to a doubling time of about **3.1 days**.
- European countries experienced substantially different reported mortality burdens during the first wave.
- GDP per capita, life expectancy, healthcare capacity, age structure, and urbanization are strongly correlated across countries.
- PCA shows that the first two components summarize **80.3%** of the variation in the selected development indicators.
- The cross-country mortality model achieves an **adjusted R² of 0.560**, indicating meaningful but incomplete alignment between mortality and structural country characteristics.
- Cross-country results are descriptive and should not be interpreted as evidence of causality.

## 🛠️ Technologies Used

- R
- Quarto
- tidyverse
- dplyr
- ggplot2
- tidyr
- broom
- janitor

## 📁 Repository Structure

```text
COVID19-Data-Analysis-R/
├── data/
│   ├── WHO-COVID-19.csv
│   └── WDI.csv
├── report.qmd
├── COVID19_Data_Analysis_R.html
├── README.md
└── .gitignore
```

## 📓 Full Analysis

The complete analysis is available in:

- `report.qmd` — complete reproducible R/Quarto analysis
- `COVID19_Data_Analysis_R.html` — rendered HTML report with figures, tables, results, and foldable code

The HTML report presents the full project in a portfolio-friendly format while allowing the underlying R code to be viewed when needed.

## ⚠️ Limitations

Several limitations should be considered when interpreting the results.

Reported COVID-19 cases and deaths depend on testing capacity, reporting systems, case definitions, and certification practices, all of which varied across countries and over time.

The analysis also uses country-level aggregate data. Relationships observed between socioeconomic indicators and mortality therefore represent **ecological associations** and cannot establish individual-level or causal effects.

Some World Bank indicators contain missing values, which reduces the number of countries available for PCA and regression analyses.

The relationship between reported cases and deaths also changed throughout the pandemic because of vaccination, variants, treatment improvements, testing availability, demographic changes, and other factors.

Future work could incorporate age-specific outcomes, vaccination coverage, healthcare-system pressure, and policy timing.

## 👩‍💻 Author

**Aya Abdine**

MSc Data Science for Society and Business  
Constructor University, Bremen, Germany