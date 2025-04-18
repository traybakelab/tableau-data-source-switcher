# tableau-data-source-switcher

This script switches data sources within a Tableau workbook by modifying its `.twb` file. It leverages the fact that `.twb` files are XML-based and can be parsed and edited as such.

What it does:
- Connects to Tableau Cloud using the REST API
- Downloads a specified workbook
- Extracts and parses the `.twb` file from the `.twbx` file
- Replaces specified elements using a CSV-based mapping table
- Saves a new `.twbx` file with the updated `.twb` inside

Note that this project is a work in progress. Some improvements are planned, such as:
- Refactoring update_twb_values() for better modularity
- Including an upload of the updated .twbx file into the specified project (environment)

---

How it works

The script looks for and replaces the following elements in the workbook's .twb file:

- `caption` – the data source display name
- `id` – the data source ID (often used internally)
- `dbname` – the database name used in the connection string

These values must be defined in the mapping table (`.csv`) included in the repo. The are currently extracted manually into a mapping table which servers as a master file for lookup and replacement values for each data source. 

REQUIREMENTS
pip install pandas
pip install requests
