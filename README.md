# Prostate Cancer Big Data Analytics Pipeline

## Project Overview

This project implements a **Big Data analytics pipeline for prostate cancer data**, demonstrating core concepts across **data ingestion, NoSQL modeling, distributed batch processing, and velocity-oriented analytics**.

The goal is not predictive modeling, but to **design and integrate a complete Big Data architecture**, showing how heterogeneous datasets can be ingested, processed at scale, and analyzed to extract **clinically meaningful insights** related to prostate cancer severity, PSA levels, demographics, and survival outcomes.

The project follows the principles taught in Big Data systems, combining:
- Data modeling decisions
- Distributed computation (Apache Spark)
- Analytical reasoning
- Clear documentation and reproducibility

---

## Project Goals

The implementation aligns with the following objectives:

1. **Model heterogeneous prostate cancer datasets in a NoSQL database**  
   Demonstrate schema design choices and flexible document-based storage using MongoDB.

2. **Apply batch processing using Apache Spark**  
   Perform distributed analytics on structured medical data using Spark SQL and DataFrames.

3. **Demonstrate streaming / velocity-oriented analytics concepts**  
   Apply micro-batch and incremental processing concepts using Spark Structured Streaming (with a documented deviation).

4. **Extract meaningful insights related to prostate cancer severity**  
   Analyze PSA trends, cancer stages, demographic factors, and survival outcomes.

5. **Demonstrate a complete Big Data architecture**  
   Integrate ingestion, storage, batch analytics, and streaming concepts into a coherent pipeline.

---

## Repository Structure

```text
prostate-cancer-big-data/
│
├── code/
│   ├── mongo_ingest.ipynb
│   ├── spark_batch.ipynb
│   └── spark_streaming(deviation).ipynb
│
├── data/
│   ├── prostate_cancer_prediction.csv
│   └── patients_records.json
│
├── README.md
```
## Datasets

### Prostate Cancer CSV Dataset
- **Source:** Kaggle  
- **Format:** Structured CSV  
- **Description:** Contains patient-level clinical and demographic attributes such as:
  - Age
  - PSA level
  - Cancer stage
  - Biopsy results
  - Lifestyle indicators
  - Survival outcome

### JSON Dataset (Derived)
- Created from the CSV dataset
- Models patients as **nested documents**, including:
  - Demographics
  - Clinical visits
  - Outcomes
- Used to demonstrate **NoSQL modeling strategies**

---

## Notebook Descriptions

### 1. `mongo_ingest.ipynb` — Data Ingestion & NoSQL Modeling

This notebook:
- Loads the CSV dataset
- Transforms selected fields into a **nested JSON document structure**
- Ingests both CSV and JSON datasets into MongoDB

It demonstrates:
- Schema flexibility
- Document-oriented modeling
- Separation of raw vs. modeled data

This notebook fulfills the **data ingestion and storage layer** of the pipeline.

---

### 2. `spark_batch.ipynb` — Batch Analytics with Apache Spark

This notebook performs distributed batch analytics using Spark.

Key analyses include:
- **Average PSA levels by cancer stage**
- **5-year survival outcomes by cancer stage**
- Demographic segmentation (age groups)
- Conversion of Spark results to Pandas for visualization

Visualizations are included to support **data storytelling**, showing how disease severity
and survival outcomes vary across patient groups.

This notebook represents the **analytics and insight extraction layer**.

---

### 3. `spark_streaming(deviation).ipynb` — Streaming Analytics (Documented Deviation)

This notebook demonstrates **velocity-oriented analytics concepts**, including:
- Micro-batch processing
- Incremental aggregation
- Conceptual streaming pipelines

Due to **Windows + Hadoop native library constraints**, full file-based streaming with
checkpointing was not reliably supported in the execution environment.  
Instead, a **controlled streaming substitute** was implemented to demonstrate:
- Continuous data arrival
- Incremental aggregation logic
- Structured Streaming APIs

This deviation is **explicitly documented** and preserves the **conceptual learning outcomes**
of streaming systems.

---

## Key Insights Extracted

### 1. PSA Levels by Cancer Stage
- PSA levels increase with disease severity
- Metastatic and advanced stages exhibit higher average PSA values
- Supports clinical expectations regarding PSA as a severity indicator

### 2. 5-Year Survival Outcomes by Cancer Stage
- Localized cancer shows the highest survival rates
- Advanced and metastatic stages show increased non-survival counts
- Highlights the importance of early detection and screening

### 3. Demographic Trends
- Age group segmentation shows consistent PSA trends
- Reinforces the role of age as a contributing risk factor

---

## Technologies Used
- **Python**
- **MongoDB**
- **Apache Spark (PySpark)**
- **Pandas**
- **Matplotlib**
- **Jupyter Notebooks**

---

## How to Reproduce the Project

1. Clone the repository
2. Ensure the following are installed:
   - Python 3.x
   - MongoDB (local)
   - PySpark
3. Start MongoDB locally
4. Run notebooks in the following order:
   1. `mongo_ingest.ipynb`
   2. `spark_batch.ipynb`
   3. `spark_streaming(deviation).ipynb`

No code modifications are required.

---

## Notes on Streaming Deviation

The streaming component intentionally documents a real-world limitation encountered when
running Spark Structured Streaming on Windows without native Hadoop binaries.

Rather than removing streaming entirely, the project:
- Explains the limitation
- Implements a substitute approach
- Preserves the conceptual goals of streaming analytics

This reflects **realistic Big Data system constraints and design decision-making**.

---

## Conclusion

This project demonstrates a **complete Big Data analytics pipeline**, integrating ingestion,
NoSQL storage, batch analytics, and streaming concepts to extract meaningful insights from
prostate cancer data.

The focus is on **system design, scalability, and analytical reasoning**, rather than machine
learning, aligning closely with Big Data engineering principles.
