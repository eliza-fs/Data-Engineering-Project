# Automated End-to-End Data Pipeline for Online Retail Analytics

Group project for Data Engineering, BINUS University (3-person team).

## Overview

Raw retail transaction data is full of duplicates, missing values, and invalid entries (such as negative prices and quantities), so it can't be analyzed directly. This project builds an automated ETL pipeline for the **Online Retail II** dataset (~400K transactions, 2010-2011) and delivers the cleaned data to interactive Power BI dashboards.

## My Role

Data curation and validation, Power BI dashboard design and visualization, and research paper writing.

## Architecture

```
CSV → Pentaho PDI (ETL) → MySQL (staging + star schema) → Power BI
```

- **ETL:** Pentaho Data Integration; deduplication with Unique Rows (HashSet), business-rule filtering, and incremental loading
- **Data model:** star schema with one sales fact table and four dimensions (customer, product, country, time)
- **Automation:** Pentaho Job loads all dimensions before the fact table, run daily via `Kitchen.bat` and Windows Task Scheduler

## Tech Stack

Pentaho Data Integration, MySQL, Power BI

## Dataset

Not included in this repo. Download **Online Retail II** from [Kaggle]([https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci](https://www.kaggle.com/datasets/tunguz/online-retail-ii)) and check its license before reuse.

## Key Results

- **$8.75M** revenue across **5M units** sold
- **Paper Craft** is the largest revenue-contributing product category; the UK leads in sales volume
- Customer retention drops sharply after the first month (**11%-36%** across cohorts), suggesting a need for early post-purchase retention campaigns
- **EIRE** has the highest average revenue per customer (~$100K)


```

## Future Work

Migrate the pipeline to a distributed framework such as Apache Spark to support real-time or streaming data.
