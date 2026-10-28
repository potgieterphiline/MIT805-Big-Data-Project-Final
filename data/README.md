# Dataset: NYC Yellow Taxi Trip Records

The data is not stored in this repository because of its size. Download it from the original source.

- Source: NYC Taxi and Limousine Commission (TLC), https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
- Terms of use: https://www.nyc.gov/home/terms-of-use.page
- Data dictionary: https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf

Each month is one Parquet file named `yellow_tripdata_YYYY-MM.parquet`, which can be downloaded from the TLC page or from:

```
https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_YYYY-MM.parquet
```

Part 1 uses January 2014 to December 2025, and Part 2 uses January 2024 to December 2025. Part 2 also uses the zone lookup file, which turns zone numbers into names:

```
https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv
```

The download code is in `notebooks/01_data_collection.ipynb`.
