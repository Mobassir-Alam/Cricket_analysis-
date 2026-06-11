CRICKET ANALYSIS PROJECT:

Analysis of 5,000+ ODI player records across batting and bowling datasets using SQL Server.
This project covers the full data pipeline — from raw CSV ingestion to a cleaned schema and business questions.


Project Structure:

Cricket-Analysis-SQL/
- tables_for_csv.sql                      # Raw staging tables for CSV import
- bulk_insert.sql                         # Stored procedure to bulk load CSVs
- creating_tables_for_cleaned_data.sql    # Clean schema table definitions
- data_cleaning.sql                       # Stored procedure for data transformation
- Main_Analysis.sql                       # All business questions & analysis queries
- README.md


Data sourced from Kaggle.com.


Tools Used:

SQL Server — data storage, cleaning, and analysis
SQL Server Management Studio (SSMS) — query execution



Data Pipeline:

Raw CSVs → Bulk Insert (Stored Proc) → Raw Tables
              ↓
    Data Cleaning (Stored Proc)
              ↓
    Clean Tables (odi.batting_clean, odi.bowling_clean)


Cleaning steps performed:

Extracted country name from player column using CHARINDEX
Normalized inconsistent country codes (e.g. Asia/ICC/SL → SL, AUS/ICC → AUS)
Handled null values stored as '-' across average, strike rate, and economy columns
Removed duplicate player entries using ROW_NUMBER() OVER (PARTITION BY player)
Derived new columns: debut_year, last_played, years_played


Key Findings:

Sachin Tendulkar (INDIA) is the all-time leading run-scorer with 18,426 runs in 463 matches
Muttiah Muralitharan (SL) tops the wicket-takers chart among bowlers with 100+ matches
Bowlers classified as "economical" (economy < 4.0) are almost exclusively from the pre-2000 era


How to Run This Project:

-Install SQL Server Express and SSMS (both free)
-Create a database and run tables_for_csv.sql
-Update the file path in 2_bulk_insert_proc.sql to your local CSV location
-Run EXEC cricket_data to load raw data
-Run creating_tables_for_cleaned_data.sql
-Run EXEC cricket_tables to clean and transform the data
-Open Main_Analysis.sql and run any query




Mohd Mobassir Alam
Data Analyst | SQL · Power BI · Excel
mobassir7410@gmail.com

