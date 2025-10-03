# SQLite_database  
# 🔹 1. Libraries Imported

The notebook uses:

1)sqlite3 – for database creation and queries

2)pandas – for loading SQL results into a DataFrame

3)matplotlib.pyplot – for plotting charts  
# 🔹 2. Database Setup

A SQLite database named sales_data.db is created.

The existing sales table (if any) is dropped:

DROP TABLE IF EXISTS sales


A new table is then created:

CREATE TABLE sales (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    product TEXT,
    quantity INTEGER,
    price REAL
)


# 🔹 3. Sample Data Inserted

The notebook inserts sample sales data into the table. Each row contains:

Product name

Quantity

Price per unit

Example entries (inferred from code):

('Laptop', ...)
('Phone', ...)
('Tablet', ...)
...


The insert command uses:

cursor.executemany(
    "INSERT INTO sales (product, quantity, price) VALUES (?, ?, ?)", 
    sample_data
)

# 🔹 4. SQL Query & Data Extraction

A query is executed to calculate total revenue per product by multiplying quantity * price:

SELECT 
    product, 
    SUM(quantity) AS total_quantity,
    SUM(quantity * price) AS total_revenue
FROM sales
GROUP BY product;


The result is loaded into a Pandas DataFrame using:

df = pd.read_sql_query(query, conn)

# 🔹 5. Output & Visualization

The notebook:

Prints the sales summary DataFrame

Creates a bar chart showing revenue per product

There's also commented code to save the image:

# plt.savefig("sales_chart.png")

# ✅ Final Summary

Your notebook successfully:

Created a sales database

Inserted sample sales data

Queried total quantity and revenue by product

Displayed results using Pandas

Visualized sales revenue using Matplotlib

If you want a written explanation, a PowerPoint report, or a PDF summary, just tell me which format you need and I’ll create it immediately—no extra questions! 
