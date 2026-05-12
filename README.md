# ACS County-Level Analysis

A collaborative R-based data wrangling and visualization project analyzing shifts in county-level demographics across the United States using American Community Survey (ACS) DP05 1-year data from 2019, 2021, 2022, 2023, and 2024.

## Project Overview

This project examines how county-level demographic patterns changed across the United States over time. Using ACS DP05 demographic and housing estimates, the analysis explores where population is growing or declining, which regions are aging fastest, how racial and ethnic composition is shifting, and how housing availability and sex-ratio outliers vary across counties.

The project was developed for **INSS 615 – Data Wrangling for Visualization** in Spring 2026.

## Business Problem

A national policy research institute asked the team to analyze five years of county-level demographic data and generate findings that could support decision-making related to:

- education
- housing
- healthcare
- infrastructure
- resource allocation

### Core Questions

1. Which U.S. counties and Census regions saw the largest population increases or decreases from 2019 to 2024?
2. How is county age structure changing, and which regions are aging fastest?
3. How have racial and ethnic compositions shifted over time?
4. What is the relationship between total population and housing units?
5. Which counties are outliers in sex ratio, and are those outliers associated with region or population size?

## Dataset

**Source:** ACS DP05 – Demographic and Housing Estimates (1-Year), U.S. Counties, 2019–2024

### Original Dataset Size
- **4,306 rows**
- **114 columns**

### Final Prepared Dataset
- **4,240 rows**
- **39 columns**

### Example Variables Used
- `survey_year`
- `geo_id`
- `county_name`
- `state_name`
- `total_population`
- `median_age`
- `sex_ratio`
- `population_under_18`
- `population_65_and_over`
- `white_alone`
- `black_alone`
- `asian_alone`
- `hispanic_latino`
- `total_housing_units`
- `region`
- `division`

### Derived Variables
- `senior_pop_share`
- `working_age_pop_share`
- `youth_pop_share`
- `housing_to_pop`
- `pop_change_tier`
- `diversity_tier`
- `diversity_index`

## Data Preparation

The team combined five ACS DP05 files into a single longitudinal dataset for analysis.

Major preparation steps included:

- loading raw Census files as character values to preserve special ACS entries such as `N`, `(X)`, and blanks
- removing extra label rows included in source files
- validating and remapping inconsistent DP05 variable codes across years, especially for 2024
- renaming fields to a consistent naming convention
- converting analysis fields to numeric types
- parsing the original geographic label into standardized `county_name` and `state_name`
- replacing placeholder values with `NA`
- imputing missing numeric values using median values within survey year and Census region

## Tools Used

- **R**
- **R Markdown**
- Data wrangling and visualization workflows in a knitted `.Rmd` output

## Key Findings

### 1. Mainland regions generally grew, while Puerto Rico declined
All mainland U.S. regions showed net growth from 2019 to 2024, though growth was uneven across counties. Puerto Rico showed notable instability and decline. The South had the highest concentration of high-growth counties, while the Midwest and West showed more mixed patterns.

### 2. All regions aged over time
All regions became older between 2019 and 2024. Puerto Rico was both the oldest region in the study and the fastest-aging, with median age increasing from 43 to 45. Youth population share declined across every region.

### 3. Diversity patterns varied by region
Puerto Rico and parts of the South and West showed higher diversity overall. The Midwest had the largest concentration of low- and moderate-diversity counties. Regional racial and ethnic patterns changed gradually rather than dramatically over time.

### 4. Housing-to-population ratios were mostly stable, with Northeast outliers
Most counties had similar housing-to-population ratios, with a national median of 0.43. The distribution was right-skewed, and the Northeast had the largest share of high-ratio outliers.

### 5. Sex-ratio outliers were concentrated in smaller counties
Regional average sex ratios remained relatively stable, but extreme outliers tended to occur in counties with small populations. Larger counties showed more balanced sex ratios.

## Recommendations

Based on the analysis, the team recommended that policymakers:

- direct infrastructure and service investments toward fast-growing mainland counties
- support stabilization efforts in declining areas such as Puerto Rico
- expand aging and workforce-retention policies
- use regional diversity patterns to inform equitable service delivery
- study Northeast housing anomalies more closely
- further investigate sex-ratio outliers in small counties

## Challenges and Limitations

This project involved substantial preprocessing challenges due to inconsistent ACS DP05 variable structures across years, especially in 2024. Some counties were excluded from the 2019 and 2024 source files, which limited parts of the population-change analysis. A small number of race-related values became unrealistic after imputation and were removed from diversity analysis rather than retained.

## Team

- Dallas James
- Warren Jones
- Jonatan Tobon

## Repository Contents
```text
.
acs-county-level-analysis/
├── ACSCountyLevelAnalysis.Rmd
├── Written Report Group 1 Final.docx
├── data/
│   ├── ACSDP1Y2019.DP05-Data.csv
│   ├── ACSDP1Y2021.DP05-Data.csv
│   ├── ACSDP1Y2022.DP05-Data.csv
│   ├── ACSDP1Y2023.DP05-Data.csv
│   └── ACSDP1Y2024.DP05-Data.csv
├── outputs/
│   └── ACSCountyLevelAnalysis.html
└── README.md
