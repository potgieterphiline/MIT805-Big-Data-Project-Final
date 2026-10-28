# MIT805 Big Data Project

**Group 16**

## Group Members

- Philine Potgieter
- Tshwanelo Mathala

## Project Overview

This project analyses NYC Yellow Taxi trip records to explore night-time travel demand, fare behaviour and data quality between 2014 and 2025. Part 1 covers dataset collection, data preparation, exploratory data analysis and evaluation against the 7 Vs of Big Data.

Part 2 uses PySpark on the 2024 and 2025 records to find the pickup zones with the lowest average night-time speeds, and the hours at which this happens. The trips are transformed, grouped by zone and hour, and aggregated, which demonstrates Spark's distributed processing and DAG execution. The results point to possible congestion hotspots at night.

## Dataset

The project uses the **NYC Yellow Taxi Trip Records** published by the NYC Taxi and Limousine Commission (TLC). Part 1 covers January 2014 to December 2025, and Part 2 uses the 2024 and 2025 files only.

Source: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page  
Terms of use: https://www.nyc.gov/home/terms-of-use.page

| Level | Size | Files | Period |
|---|---|---|---|
| Raw (full TLC archive) | 29.66 GB | 204 monthly Parquet files | Jan 2009 to Dec 2025 |
| Working | 12.93 GB | 144 | Jan 2014 to Dec 2025 |
| Processing (Part 1) | 4.96 GB | 143, night-time trips only (8pm to 5am) | Jan 2014 to Dec 2025 |
| Subset (Part 2) | [size] GB | 24 | Jan 2024 to Dec 2025 |

The data is not stored in this repository because it exceeds GitHub's file size limits. Download instructions are in `data/README.md`.

## Repository Structure

```
project/
├── README.md
├── requirements.txt
├── data/
│   └── README.md        dataset source and download instructions
├── notebooks/           Part 1 and Part 2 code
├── src/                 reusable scripts (if any)
├── output/              preparation steps and summary tables
├── figures/             charts used in the reports
└── report/              Part 1 and Part 2 reports (PDF)
```

## Part 1: Data Collection and Analysis

- Data preparation and quality: `notebooks/[preparation notebook]`, with the steps and reasoning in `output/[preparation steps file]`.
- Exploratory data analysis: `notebooks/[EDA notebook]`, with summary tables in `output/[EDA tables file]` and charts in `figures/` (files starting with `part1_`).
- Report: `report/[part 1 report].pdf`

## Part 2: PySpark and MapReduce

- **Map:** the hour, pickup zone and trip duration are created for every trip.
- **Shuffle:** trips are grouped by pickup zone and hour, and by month for the trend over time.
- **Reduce:** miles and seconds are added up for each group, and the average speed is calculated from those totals.

Code is in `notebooks/[MapReduce notebook]` and `notebooks/[visualisation notebook]`. The Spark execution plan is printed with `explain` in the MapReduce notebook. Charts are in `figures/` (files starting with `part2_`).

- Report: `report/[part 2 report].pdf`
- Video demo:https://drive.google.com/file/d/1A4NJ1M9yupDZxiiTPd6NtBVYYN7PC0o4/view?usp=drivesdk
## How to Reproduce

1. Clone this repository.
2. Install the dependencies with `pip install -r requirements.txt`.
3. Download the data as described in `data/README.md` and upload it to your Google Drive.
4. Open the notebooks in Google Colab and run them in numerical order, updating the Drive path at the top of each notebook.

## Notes

- The notebooks were written for Google Colab and mount Google Drive, so the file paths are specific to Colab.
- The data contains no personally identifiable information.
