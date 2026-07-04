# PartnerCompanyProject_03_KMeans
The project objective is to integrate multiple datasets (product, segment, category, and sales), perform data cleaning, and prepare a unified analytical dataset for subsequent modeling and business insights.

## Project Overview
This project is part of the EBAC Data Science & Business Analytics Program and corresponds to Deliverable 03 of the Proyecto Empresa Aliada.
The objective is to integrate multiple datasets (product, segment, category, and sales), perform data cleaning, and prepare a unified analytical dataset for subsequent modeling and business insights.

The notebook includes:
- Loading and inspecting dimension and fact tables
- Cleaning and transforming product and sales data
- Merging datasets into a single analytical table
- Exploratory checks of weekly sales behavior

## Project Structure
Code:

Proyecto_empresa_aliadaEntregable03/
│
├── DIM_PRODUCT.xlsx
├── DIM_SEGMENT.xlsx
├── DIM_CATEGORY.csv
├── FACT_SALES.csv
│
├── Proyecto_empresa_aliadaEntregable03.ipynb   ← Main notebook
└── README.md

## Data Sources
1. DIM_PRODUCT.xlsx
Contains product-level attributes:
- Manufacturer
- Brand
- Item code
- Description
- Category
- Format
- Attributes (ATTR1, ATTR2, ATTR3)

2. DIM_SEGMENT.xlsx
Provides segment classification based on product attributes:
- Category
- Format
- ATTR1, ATTR2, ATTR3
- Segment

3. DIM_CATEGORY.csv
Category-level metadata.

4. FACT_SALES.csv
Weekly sales information:
- WEEK
- ITEM_CODE
- TOTAL_UNIT_SALES
- TOTAL_VALUE_SALES
- TOTAL_UNIT_AVG_WEEKLY_SALES
- REGION

Example:

Code
WEEK   ITEM_CODE        TOTAL_UNIT_SALES   TOTAL_VALUE_SALES   REGION
34-22  7501058792808BP2 0.006              0.139               TOTAL AUTOS AREA 5

## Methods & Workflow
1. Data Loading
The notebook loads all dimension and fact tables using pandas.read_excel() and pandas.read_csv().

2. Data Cleaning & Preparation
Key steps include:
- Inspecting product and sales tables
- Handling missing values
- Standardizing formats
- Preparing keys for merging

3. Dataset Merging
Two main merges are performed:

Merge 1: Product + Segment
python
df_full = df_prod.merge(
    df_seg,
    how="left",
    left_on=["CATEGORY", "ATTR1", "ATTR2", "ATTR3", "FORMAT"],
    right_on=["CATEGORY", "ATTR1", "ATTR2", "ATTR3", "FORMAT"]
)
Merge 2: Adding Sales
python
df_full = df_full.merge(
    df_sales,
    left_on="ITEM",
    right_on="ITEM_CODE",
    how="left"
)
Resulting dataset includes:

Product attributes

Segment classification

Weekly sales metrics

Region information

Example merged output (from your notebook):

Code
MANUFACTURER   BRAND     ITEM        CATEGORY   FORMAT   SEGMENT   WEEK   TOTAL_UNIT_SALES   REGION
INDS. ALEN     CLORALEX  0000075000592 1        LIQUIDO  BLEACH    45-22  0.034              TOTAL AUTOS SCANNING MEXICO
📈 Exploratory Analysis
The notebook includes initial checks such as:

Weekly sales distribution

Product-level sales behavior

Segment-level comparisons

This prepares the dataset for future modeling (clustering, PCA, forecasting, etc.).

⚙️ Environment Setup
Required Libraries
Code
pandas
numpy
matplotlib
seaborn
scikit-learn
Install Dependencies
bash
pip install pandas numpy matplotlib seaborn scikit-learn
▶️ How to Run the Notebook
Open JupyterLab or Jupyter Notebook.

Place all data files in the same directory as the notebook.

Run the notebook sequentially from top to bottom.

Ensure all datasets load correctly before executing merge operations.

📌 Next Steps (Deliverable 04 and beyond)
Perform deeper exploratory analysis

Build segmentation models (KMeans, PCA)

Create dashboards in Power BI

Generate business insights for the partner company
