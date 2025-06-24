# DSA2040A Mid Semester Examination Summer 2025

## Project Overview

The project uses WSL Ubuntu 24.04 OS with default configurations as the operating system environment.

## ETL Phases

The project is run in three Jupyter Notebooks each covering the three phases of ETL:

- Extract
- Transform
- Load

### Extract

Extraction is done in the `etl_extract.ipynb` file.

In extraction the `raw_data.csv` and `incremental_data.csv` files are read into Pandas dataframes. Afterwards, the rows and columns of the dataframes are displayed alongside information about the data types and null values for each column in the dataframe. The Pandas dataframes are then saved back into the original files from which they were obtained.

### Transform

Transformation is done in the `etl_transform.ipynb` file.

In transformation, the `raw_data.csv` and `incremental_data.csv` files are read into Pandas dataframes. Helper functions for ease of transformation are detailed soon after. Before any transformation is done the two loaded dataframes are displayed one after the other.

The transformations are done in two phases:

- Data cleaning
- Data enrichment

In the data cleaning phase:

- Irrelevant columns are dropped
- Null values are imputed
- Duplicate columns are dropped

In the data enrichment phase:

- Datetime columns are changed to human readable format
- Summary statistic columns are computed

In the imputation of null values graphs showing the skewness of the distribution are employed to offer evidence as to why the chosen method of imputation is employed. For each transformation the before and after of the dataframe is shown.

Finally, the data is saved into the `transformed_full.csv` and `transformed_incremental.csv` files.

### Loading

Loading is done in the `etl_load.ipynb` file.

In loading, the `transformed_full` and `transformed_incremental` files are read into Pandas dataframes. Connections to the SQLite databases are established. The dataframes are then saved to the SQLite databases `full_data.db` and `incremental_data.db`.

To validate that they have been effectively saved the stored results are previewed for both SQLite databases. Finally, the connections to the SQLite databases are closed.

## Tools Used

A Jupyter Notebook is employed. Python 3.12 within a virtual environment is run as the kernel for the Jupyter Notebook instance. The modules employed are detailed in the `requirements.txt` file. The modules shown do not include the Python standard library modules.

## How to Run

1. Create the virtual environment and activate it.

```bash
python3 -m venv .venv
source .venv/bin/activate
which python 
```

2. Download the needed modules.

```bash
pip install -r requirements.txt
```

3. For each Jupyter Notebook, open the Jupyter Notebook and select the virtual environment's Python version as the kernel from which the Jupyter Notebook will base its instance.

4. Run all the code blocks. This will offer output with which to understand the explanations offered.

## Screenshots

For the raw data the skewness of the quantitative columns is:

![Raw Data Null Value Imputation](/raw_data_skewness.png)

For the incremental data the skewness of the quantitative columns is:

![Incremental Data Null Value Imputation](/incremental_data_skewness.png)

The preview of the transformed data loaded into the SQLite databases is:

![Preview of Stored SQLite Data](/preview_stored_data.png)
