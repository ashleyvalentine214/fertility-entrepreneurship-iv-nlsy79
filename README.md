# Fertility and Female Entrepreneurship: Evidence from an Instrumental Variables Approach Using Twin Births in the NLSY79

Repository name: `fertility-entrepreneurship-iv-nlsy79`

## Project Overview

This repository contains the final report PDF and R Markdown file for an econometrics final project studying whether fertility affects female entrepreneurship and labor market outcomes. The paper uses the National Longitudinal Survey of Youth 1979 (NLSY79) and uses twin/triplet births as an instrument for fertility. The main outcome is self-employment in 2022, with employment and wage income examined as additional labor market outcomes.

The project asks:

> Does fertility affect female entrepreneurship and labor market outcomes, using twin births as an instrument for fertility?

## Data

The two large CSV data files are not included in the public GitHub repository because they were provided separately by the instructor for this project, are too large for normal GitHub upload, and should not be publicly redistributed without explicit permission.

To reproduce the analysis, obtain the required data files from the instructor or original NLSY source and place them in the `data/` folder before knitting the R Markdown file. The Rmd expects the following exact file names:

- `NLSY79_TwinIV_Mother_Entrep_v1.csv`
  - Main NLSY79 respondent-level extract used to construct fertility, twin/triplet births, class-of-worker/self-employment, employment, income, education, parental education, marital status, and race variables.

- `NLSY79_TwinIV_Mother_Entrep_v1-value-labels.do`
  - Rename and value-label file used to identify groups of NLSY79 variables, especially repeated twin/triplet birth indicators and longitudinal class-of-worker variables.

- `NLSCYA_TwinPair_Kinship_v1.csv`
  - NLS Children and Young Adults linked child file used to construct the approximate respondent age measure and the exploratory longitudinal childbirth-timing extension.

The small `.do` value-label file may be included in the repository for transparency if permitted. The two large CSV files should be omitted from the public repository unless the instructor gives permission to share them.

## Methodology

The analysis includes:

- Ordinary least squares (OLS) estimates relating fertility to self-employment, employment, and wage income.
- Instrumental variables/two-stage least squares (2SLS), using an indicator for ever having a twin/triplet birth as an instrument for number of children.
- A broader entrepreneurship robustness check that includes self-employment or working in a family business.
- Education heterogeneity analysis comparing BA+ and non-BA women.
- One-to-one nearest-neighbor propensity score matching with replacement as a robustness check.
- An exploratory appendix analysis using longitudinal class-of-worker histories to measure entry into self-employment after childbirth.

## Repository Structure

```text
fertility-entrepreneurship-iv-nlsy79/
|-- README.md
|-- ECI_Final_Research_Project_Ashley.Rmd
|-- ECI_Final_Research_Project_Ashley.pdf
`-- data/
    |-- NLSY79_TwinIV_Mother_Entrep_v1-value-labels.do
    |-- NLSY79_TwinIV_Mother_Entrep_v1.csv              # not included publicly
    `-- NLSCYA_TwinPair_Kinship_v1.csv                  # not included publicly
```

## Software Requirements

The project is written in R Markdown and uses mostly base R.

Required R packages:

- `rmarkdown`
- `knitr`

The PDF output also requires a working LaTeX installation. The document uses common LaTeX packages including `setspace`, `booktabs`, `makecell`, `etoolbox`, `needspace`, and `float`.

## Reproducing the Analysis

1. Clone the repository.

   ```bash
   git clone https://github.com/your-username/fertility-entrepreneurship-iv-nlsy79.git
   cd fertility-entrepreneurship-iv-nlsy79
   ```

2. Obtain the required data files from the instructor or original NLSY source and place them in the `data/` folder using the exact file names listed above.

3. Open `ECI_Final_Research_Project_Ashley.Rmd` in RStudio.

4. Knit the R Markdown file to PDF.

The Rmd reads the data from relative paths inside `data/`, constructs all analysis variables, runs the regressions and robustness checks, and generates the final PDF tables and appendix tables.

## Main Findings

The first-stage results show that twin/triplet births strongly predict fertility. The main IV estimates for self-employment, employment, and earnings are imprecise and statistically insignificant. The self-employment point estimates are often positive, including in the baseline IV and matching specifications, but the evidence should be interpreted as suggestive rather than conclusive. The larger-sample robustness check is reported as a sensitivity check because it changes the control set and is more vulnerable to fertility-measure construction issues.

## Notes

Appendix Table A5 is an exploratory longitudinal extension. It measures whether first observed self-employment occurs after first childbirth, excluding women already self-employed before childbirth and excluding same-year ambiguous cases. This appendix result is included for transparency and future research motivation; it is not the primary specification and does not replace the main 2022 self-employment analysis.
