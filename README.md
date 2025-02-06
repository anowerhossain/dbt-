# How to Run Your First dbt Project 🚀
Follow these steps to install, configure, and execute your first dbt project.

### 1️⃣ Install dbt
🔹 Install dbt Core using `pip`

```bash
pip install dbt-core
```

🔹 Install a dbt adapter for your data warehouse

```bash
pip install dbt-postgres
```

🔹 Check if dbt is installed correctly

```bash
dbt --version
```

### 2️⃣ Initialize a New dbt Project

🔹 Create a new dbt project by running

```bash
dbt init reve_dbt
```
🔹 File Structure

```bash
my_first_project/
│── dbt_project.yml      # Main dbt project configuration file
│── models/              # Stores SQL transformation models
│   ├── example/         # Example models directory
│   │   ├── my_first_dbt_model.sql   # First dbt model
│   │   ├── my_second_dbt_model.sql  # Second dbt model
│── seeds/               # CSV files for seeding data into dbt
│── macros/              # Custom macros (reusable SQL functions)
│── tests/               # Custom tests for data validation
```

🔹 Navigate into the project folder:

```bash
cd reve_dbt
```

🔹 Test the Connection

```bash
dbt debug
```

### 3️⃣ Run Your First dbt Model

🔹 Config Block:
```sql
{{ config(materialized='table') }}
```
- This tells dbt how to store the results.
- materialized='table' means dbt will create a table in the database.

You can change it to view to create a view instead:

```sql
{{ config(materialized='view') }}
```

- Table: Stores data physically (faster queries, but takes up storage).
- View: Stores only the SQL logic (faster updates, but queries may be slower).

```sql
SELECT id, name, email
FROM your_source_table
```

### 4️⃣ Run this model using

```bash
dbt run
```

- If this file is named my_first_dbt_model.sql, the result will be stored in the database as:

🔹 A table (my_schema.my_first_dbt_model)

🔹 A view (my_schema.my_second_dbt_model)

- If you want to run only a specific model like my_first_dbt_model.sql

```bash
dbt run --select my_first_dbt_model
```

- If you want to run only a specific models pattern like my_*

```bash
dbt run --select my_*
```

### 4️⃣ Run models test using 

- Test all the models
```bash
dbt test
```
- Test only a specific model

```bash
dbt test --select my_first_dbt_model
```

### 🌱 Understanding dbt Seeds (`dbt seed`)
dbt Seeds allow you to load small, static CSV files into your database. This is useful for reference data, mapping tables, or small datasets that don’t change often.

- Place CSV files inside the seeds/ directory.
- Run dbt seed to load them into the database.
- The CSV data becomes a table in your database.
- Use it in models just like any other table.

Create a CSV File (`categories.csv`) in seeds/ directory

```csv
id,name,type
1,Electronics,Gadgets
2,Furniture,Home
3,Clothing,Fashion
4,Books,Education
```

Run dbt seed

```bash
dbt seed
```
This loads categories.csv into the database as a table name `categories`.

- If you have a seed file named customers.csv inside the seeds/ folder, run:

```bash
dbt seed --select customers
```

- If you have multiple seed files named customers.csv and orders.csv inside the seeds/ folder, run:

```bash
dbt seed --select customers orders
```

- If your seed files are inside a subfolder, for example

```bash
seeds/
│── staging/
│   ├── customers.csv
│   ├── orders.csv
│── products.csv
```

```bash
dbt seed --select staging.*
```


```bash
dbt seed --full-refresh
```
--full-refresh ensures that the old incorrect table is dropped and replaced with the corrected CSV data.



