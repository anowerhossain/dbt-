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

reve_dbt/

│── dbt_project.yml

│── models/

│   ├── example/

│   │   ├── my_first_dbt_model.sql

│   │   ├── my_second_dbt_model.sql

│── seeds/

│── macros/
│── tests/


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

```
dbt run
```

- If this file is named my_first_dbt_model.sql, the result will be stored in the database as:
🔹 A table (my_schema.my_first_dbt_model)

🔹 A view (my_schema.my_second_dbt_model)
