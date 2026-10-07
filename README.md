# Exploratory Data Analysis of Global Economic Indicators

An exploratory data analysis (EDA) of World Bank data for **217 countries from 2000 to 2023**, covering GDP, population, life expectancy, unemployment and energy use. The project is built in Python with pandas, NumPy and matplotlib.

## Objective
To explore how countries differ in economic size, income, health and employment, and to test whether a large economy also means a high standard of living.

## Dataset
- **Source:** [World Bank World Development Indicators (WDI)](https://datatopics.worldbank.org/world-development-indicators/)
- **Download:** https://databank.worldbank.org/data/download/WDI_CSV.zip
- **Files used:** `WDICSV.csv` (main data), `WDICountry.csv` (region and income group)
- **Indicators analysed:**

| Column | Indicator | World Bank code |
|---|---|---|
| `gdp_total` | GDP (current US$) | NY.GDP.MKTP.CD |
| `gdp_per_capita` | GDP per capita (constant US$) | NY.GDP.PCAP.KD |
| `population` | Total population | SP.POP.TOTL |
| `gni_per_capita` | GNI per capita (US$) | NY.GNP.PCAP.CD |
| `energy_use` | Energy use per capita (kg oil equivalent) | EG.USE.PCAP.KG.OE |
| `life_expectancy` | Life expectancy at birth (years) | SP.DYN.LE00.IN |
| `unemployment` | Unemployment (% of labour force) | SL.UEM.TOTL.ZS |

> The raw WDI files are large (`WDICSV.csv` is about 190 MB), so they are **not included** in this repository. Download them from the link above. The cleaned dataset is included in `data/clean/`.

## Project Structure
```
world-economic-indicators-eda/
├── data/
│   ├── raw/        # original WDI files (backup, not uploaded to GitHub)
│   └── clean/
│       └── world_indicators_clean.csv
├── eda_world_indicators.ipynb
├── .gitignore
└── README.md
```

## Sprint 1: Data Cleaning
1. Saved a **raw data backup** before making any changes.
2. Merged the main data file with the country file using `Country Code`.
3. Removed regional aggregates (World, South Asia, etc.), keeping 217 real countries.
4. Selected 7 indicators and 2000 to 2023, then reshaped years from columns into rows.
5. Checked missing values (energy use 29%, unemployment 14%). Filled gaps only between known values and left the rest as missing.
6. Checked duplicates (none) and data types, then saved the clean file.

Raw shape `(396970, 70)` became clean shape `(5208, 12)`.

## Sprint 2: Analysis Questions and Findings
| # | Question | Finding |
|---|---|---|
| 1 | Highest GDP | The US ($26T) and China ($18T) lead. India is 5th at $3.25T. |
| 2 | Highest GDP per capita | Small wealthy places: Monaco, Bermuda, Luxembourg. |
| 3 | India's GDP over time | About 7 times larger ($0.47T to $3.50T), with dips in 2008 and 2020. |
| 4 | Largest GDP growth | Guyana leads. China is the only large economy in the top 10. |
| 5 | Population vs GDP | Strong positive link (0.81, log scale). |
| 6 | GDP per capita vs life expectancy | Strong positive link (0.80), with diminishing returns at high incomes. |
| 7 | Unemployment across countries | Ranges from near 0% to over 36%, highest in southern Africa. |
| 8 | High GDP, low GDP per person | India, Indonesia and Brazil. |
| 9 | Indicators over time | GDP per capita and life expectancy rose, with a dip in 2020. |
| 10 | Correlations | Only GDP and population are strongly linked. Unemployment links are weak. |

## Conclusion
A large economy does not mean a high standard of living. Income per person is the better guide, as the cases of India and China show.

## Limitations
- Some countries have no data, especially for energy use and unemployment.
- The Central African Republic's life expectancy values are unstable (18.8 in 2022 vs 57.4 in 2023), so it was flagged as an outlier.
- Correlation shows association, not cause and effect.
- Country comparisons use 2022 only.

## How to Run
1. Clone this repository.
2. Install the libraries: `pip install pandas numpy matplotlib jupyter`
3. To use the cleaned data, open the notebook and load `data/clean/world_indicators_clean.csv`.
4. To rebuild it from scratch, download the WDI files, place them in the project folder, and run Sprint 1 from the top.

## Tools
Python, pandas, NumPy, matplotlib, Jupyter Notebook, VS Code, GitHub

## Author
Archanaa, MCA, DG Vaishnav College, Chennai
