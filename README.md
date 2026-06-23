# Dunedin Climate Analysis

A data science project analysing historical weather in Dunedin, New Zealand — built around a practical question asked by a family member: *what is the weather like in Dunedin, on average?*

The end goal is a single printed poster to keep at the front door, giving a seasonal climate reference that lets someone leaving the house quickly form expectations about temperature, wind, and rainfall — without consulting a daily forecast.

Beyond its practical purpose, this project serves as a portfolio piece demonstrating applied data science across the full pipeline: data acquisition, preparation, exploratory analysis, modelling, and communication.

---

## The design principle

**Coverage over specificity.**

Rather than precise hourly predictions, the visualisations represent typical conditions across seasons and months. The most useful thing the poster communicates is the expected temperature, wind direction, and wind speed for the season or month a person finds themselves in — and whether meaningful hour-by-hour patterns exist within those seasons.

Historical data was chosen over point forecast data deliberately. A weather forecast describes what is predicted to happen on a specific future date. Historical climate data describes what has actually happened over many years — it is a more honest answer to the question "what is Dunedin weather like?" than any single forecast could be.

---

## Data

Data were obtained from [NIWA DataHub](https://data.niwa.co.nz), New Zealand's national climate database, under a **Creative Commons Attribution-NonCommercial licence**. This data may not be used for commercial purposes.

**Attribution:** Earth Sciences New Zealand (NIWA)

**Station:** Dunedin Musselburgh EWS (agent no. 15752)  
**Location:** 170.5057°E, 45.8335°S — Musselburgh, Dunedin, near the harbour  
**Full station record:** 8 August 1997 – 17 June 2026  
**Resolution:** Hourly  
**Filtered range:** 12 April 2002 – June 2026  
**Observations:** 211,616 hourly records

The Musselburgh EWS was selected over the traditional NIWA climate station for its consistent automated hourly recording across all variables of interest. The dataset was filtered to April 2002 to ensure all seven variable groups are present across a consistent time window (sunshine data begins 12 April 2002).

### Variables

| Variable | Unit | Notes |
|----------|------|-------|
| Mean temperature | °C | |
| Max / min temperature | °C | Over preceding hour |
| Grass temperature | °C | |
| Relative humidity | % | Mean over preceding minute |
| Wind speed & direction | m/s, degrees true | Mean over preceding hour |
| Gust speed & direction | m/s, degrees true | Maximum over preceding hour |
| Rainfall | mm | Cumulative over preceding hour |
| Pressure (MSL & station) | hPa | Begins 20 days after temperature record |
| Sunshine hours | hrs | Cumulative over preceding hour |
| Global horizontal radiation | MJ/m² | Ends March 2026 |

---

## Project structure

```
dunedin-climate-analysis/
├── Data/
│   └── Raw/                      # Original CSV files from NIWA (unmodified)
├── 01_data_preparation.Rmd       # Data cleaning and preparation
├── 01_data_preparation.html      # Rendered output
└── Journal.odt                   # Project planning and decision log
```

`Data/Clean/` is excluded from version control — the clean RDS file is reproducible by knitting `01_data_preparation.Rmd`.

---

## Hypotheses going into EDA

Based on knowledge of Dunedin's climate:

- **Wind:** Northerly averages in warmer months, shifting southerly in winter — with southerlies increasing through the day in colder months
- **Rainfall:** Higher in winter and spring, lower in autumn
- **Autumn:** Relatively dry with low cloud cover, despite falling temperatures — a distinct season
- **Summer:** Low winds, reasonable rainfall, higher temperatures, low cloud cover
- **Winter:** High rainfall, high cloud cover, strong southerlies, low temperatures
- **Spring:** Variable — periods of high wind and rainfall alongside rising temperatures and northerly shifts

---

## Planned visualisations (poster)

- **Wind rose** — monthly wind direction and speed
- **Temperature heatmap** — average temperatures by month and hour of day
- **Rainfall graphic** — seasonal and monthly precipitation patterns
- Possibly: sunshine hours, pressure patterns

---

## Status

| Stage | Status |
|-------|--------|
| Data acquisition | ✅ Complete |
| Data preparation | ✅ Complete |
| EDA | 🔄 In progress |
| Visualisations | ⏳ Planned |
| Poster design | ⏳ Planned |

---

## Tools

- R / RStudio
- tidyverse, lubridate, janitor
- R Markdown (fully reproducible)

---

## Reproducibility note

The data preparation stage was completed with AI assistance (Claude, Anthropic) as a learning tool — used to understand and implement pipeline steps, diagnose errors, and structure the R Markdown document. All analytical decisions — choice of data source, variables, time range, and deferral of the 10-year trimming to EDA — were made by the author. The exploratory and analytical stages are conducted independently.

---

## Licence & attribution

NIWA climate data is used under a [Creative Commons Attribution-NonCommercial licence](https://creativecommons.org/licenses/by-nc/4.0/). This project is non-commercial and is conducted for educational and portfolio purposes only.

**Data source:** NIWA DataHub — [data.niwa.co.nz](https://data.niwa.co.nz)  
**Attribution:** Earth Sciences New Zealand (NIWA)

---

*Part of a data science portfolio — Johnny Graham, Dunedin, NZ 🇳🇿*
