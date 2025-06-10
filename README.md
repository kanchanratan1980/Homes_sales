# Homes_sales

**Contributors**: Kanchan Ratan 
**Date**: June 2025

## Table of Contents
- [Home Sales Big Data Analysis with PySpark](#home-sales-big-data-analysis-with-pyspark)
  - [Table of Contents](#table-of-contents)
  - [Project Overview](#project-overview)
  - [Notebooks](#notebooks)
  - [Objective](#objective)
  - [Technologies Used](#technologies-used)
  - [Key Tasks](#key-tasks)
  - [Challenge Questions](#challenge-questions)
    - [Average Price for Four-Bedroom Houses Sold Per Year](#average-price-for-four-bedroom-houses-sold-per-year)
    - [Average Price of 3 Bed, 3 Bath, 2-Floor Homes (≥ 2000 sqft) by Year Built](#average-price-of-3-bed-3-bath-2-floor-homes--2000-sqft-by-year-built)
    - [Average Home Price by View Rating (≥ 81)](#average-home-price-by-view-rating--81)
  - [Results Summary](#results-summary)
  - [File Structure](#file-structure)
  - [How to Run](#how-to-run)
    - [Local (Windows)](#local-windows)
    - [Cloud (Colab)](#cloud-colab)
  - [Future Improvements](#future-improvements)
  - [Sources](#sources)

---

## Project Overview

This project demonstrates how to leverage PySpark for big data processing and analysis. Using a real estate dataset, we compare the performance between traditional CSV processing and Parquet formats with partitioning and caching techniques to enhance performance and scalability.

---

## Notebooks

- `Home_Sales_colab.ipynb`: Version adapted for Google Colab, suitable for cloud-based execution without local Spark/Hadoop setup.

---

## Objective

To analyze U.S. home sales data and evaluate performance differences in:
- CSV vs. Parquet formats
- Cached vs. non-cached queries
- Partitioned vs. unpartitioned Parquet storage

---

## Technologies Used

- Python (PySpark)
- Apache Spark 3.5.0
- Hadoop 3.3.x (Windows-compatible via `winutils.exe`)
- Pandas, Matplotlib (for minor local analysis)
- Jupyter Notebook / Google Colab

---

## Key Tasks

- Loaded and previewed home sales data using Spark DataFrame.
- Converted the CSV to a Spark DataFrame and created a temp view.
- Wrote and read Parquet files, with and without partitioning by `date_built`.
- Ran Spark SQL queries to:
  - Count records for specific years.
  - Filter homes based on sale price, bedrooms, and bathrooms.
  - Calculate average prices by view rating.
- Used `cache()` and timed SQL queries to benchmark performance.

---

## Challenge Questions

1. What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.
   ### Average Price for Four-Bedroom Houses Sold Per Year

| Year | Average Price (USD) |
|------|----------------------|
| 2019 | $300,263.70          |
| 2020 | $298,353.78          |
| 2021 | $301,819.44          |
| 2022 | $296,363.88          |

2. What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms? Round off your answer to two decimal places.
    ### Average Price by Year Built (3 Bed, 3 Bath, 2 Floors, ≥ 2000 sqft)

| Year Built | Average Price (USD) |
|------------|----------------------|
| 2010       | $292,859.62          |
| 2011       | $291,117.47          |
| 2012       | $293,683.19          |
| 2013       | $295,962.27          |
| 2014       | $290,852.27          |
| 2015       | $288,770.30          |
| 2016       | $290,555.07          |
| 2017       | $292,676.79          |

3. What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.
  ### Average Price of 3 Bed, 3 Bath, 2-Floor Homes (≥ 2000 sqft) by Year Built

| Year Built | Average Price (USD) |
|------------|----------------------|
| 2010       | $292,859.62          |
| 2011       | $291,117.47          |
| 2012       | $293,683.19          |
| 2013       | $295,962.27          |
| 2014       | $290,852.27          |
| 2015       | $288,770.30          |
| 2016       | $290,555.07          |
| 2017       | $292,676.79          |

4. What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.
   ### Average Home Price by View Rating (≥ 81)

| View Rating | Average Price (USD) |
|-------------|----------------------|
| 100         | $1,026,669.50        |
| 99          | $1,061,201.42        |
| 98          | $1,053,739.33        |
| 97          | $1,129,040.15        |
| 96          | $1,017,815.92        |
| 95          | $1,054,325.60        |
| 94          | $1,033,536.20        |
| 93          | $1,026,006.06        |
| 92          | $970,402.55          |
| 91          | $1,137,372.73        |
| 90          | $1,062,654.16        |
| 89          | $1,107,839.15        |
| 88          | $1,031,719.35        |
| 87          | $1,072,285.20        |
| 86          | $1,070,444.25        |
| 85          | $1,056,336.74        |
| 84          | $1,117,233.13        |
| 83          | $1,033,965.93        |
| 82          | $1,063,498.00        |
| 81          | $1,053,472.79        |


## Results Summary

- Partitioned Parquet significantly reduced I/O time, especially for filtered queries.
- Caching provided a noticeable boost for repeated queries.
- Parquet storage resulted in faster query execution and reduced memory usage vs. CSV.

---

## File Structure

```
├── Home_Sales_colab.ipynb
├── Resources/
│   ├── home_sales_revised.csv
│   └── home_sales_partitioned.parquet/
```

---

## How to Run


### Cloud (Colab)
1. Open `Home_Sales_colab.ipynb` in Google Colab.
2. Mount Google Drive or manually upload data if necessary.

---

## Future Improvements

- Automate Parquet partitioning validation.
- Visualize performance benchmarks directly in notebook.
- Integrate with cloud storage (S3 or GCS) for true big data pipeline.

---

## Sources

- [Spark Documentation](https://spark.apache.org/docs/latest/)
- [2U S3 Dataset](https://2u-data-curriculum-team.s3.amazonaws.com/)