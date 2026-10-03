# Music Store SQL — Exploratory Data Analysis

A SQL-based EDA project on a Chinook-style digital music store database, answering business questions about top customers, revenue by city and country, employee seniority, and genre/artist popularity using **MySQL**.

## 📊 About the Database

The dataset follows the classic **Chinook** music store schema, with tables including:

| Table | Description |
|---|---|
| customer | Customer profile details (name, email, etc.) |
| invoice | Purchase records, including `billing_city`, `billing_country`, and `total` |
| invoiceline | Individual line items within each invoice |
| track | Song-level data, including `name` and `miliseconds` (duration) |
| album | Album information, linked to artist |
| artist | Artist/band names |
| genre | Music genre classifications |
| employee | Staff records, including `title` and `levels` (seniority) |

## 🎯 Purpose

To practice writing and explaining multi-table SQL queries — joins, subqueries, aggregation, and filtering — to answer realistic business questions a music store might ask about its customers, revenue, staff, and catalogue.

## 🛠️ Approach

Each question is answered with a SQL query (written in two different styles where applicable), followed by a step-by-step plain-English explanation of how the query works — covering the join logic, filtering conditions, and aggregation used.

## ❓ Questions Answered

**Business & Customer Analysis**
1. Who is the senior-most employee based on job title?
2. Which countries have the most invoices?
3. What are the top 3 values of total invoice?
4. Which city has the best customers (highest total invoice revenue), for a promotional Music Festival?
5. Who is the best customer (highest total spend)?

**Music Catalogue Analysis**
6. What are the email, first name, last name, and genre of all Rock Music listeners, ordered alphabetically by email?
7. Which artists have written the most Rock music — top 10 bands by track count?
8. Which track names have a song length longer than the average song length, ordered longest first?

## 🗄️ Tech Stack

- **MySQL** — querying the Chinook-style music store database
- **Jupyter Notebook** — documenting each query alongside its explanation

## 📁 Repository Structure

```
├── musicstore_sql_EDAproject_.ipynb      # Q1-Q5: Business & customer analysis
├── music_store_sql_EDAproject_2.ipynb    # Q6-Q8: Music catalogue analysis
├── Project_Report.docx                    # Full project report
└── README.md
```

## 🚀 How to Run

1. Set up a MySQL instance and load the Chinook-style music store schema and data (`customer`, `invoice`, `invoiceline`, `track`, `album`, `artist`, `genre`, `employee` tables).
2. Open each notebook and run the SQL queries against your database connection, or copy them directly into a MySQL client (Workbench, CLI, etc.).
3. Read the explanation cell below each query for a breakdown of how it works.

## 📌 Key Query Highlights

- **Top customer identification** uses a `JOIN` between `customer` and `invoice`, grouped by `customer_id`, with `SUM(total)` to find total spend.
- **Best city for a Music Festival** is found by grouping `invoice` by `billing_city` and summing `total`, ranked descending.
- **Rock Music listeners** are found via a 4-table join chain: `customer → invoice → invoiceline → track → genre`, filtered on `genre.name = 'Rock'`.
- **Top 10 Rock bands** are found by joining `track → album → artist → genre`, grouping by artist, and counting tracks per artist.
- **Above-average song length** uses a correlated subquery — `AVG(miliseconds)` computed inside the `WHERE` clause — to filter tracks longer than the database-wide average.

---
*A SQL exploratory data analysis project on a Chinook-style digital music store database.*
