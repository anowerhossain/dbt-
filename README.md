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

🔹 Navigate into the project folder:

```bash
cd reve_dbt
```

🔹 Test the Connection

```bash
dbt debug
```

### 3️⃣ Run Your First dbt Model

```sql
SELECT id, name, email
FROM your_source_table
```

