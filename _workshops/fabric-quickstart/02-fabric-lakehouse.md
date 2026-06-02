---
title: "Fabric Quickstart — Part 2: Getting Started with Fabric Lakehouse"
description: Create a Microsoft Fabric Lakehouse, load built-in sample data, and explore the tables using the SQL analytics endpoint.
image:
  path: /assets/img/workshops/fabric-quickstart.png
  alt: Fabric Quickstart Workshop
---

## Overview

A **Fabric Lakehouse** combines the flexibility of a data lake with the structure of a data warehouse. It stores files in OneLake and surfaces Delta tables that are queryable via SQL, Spark, and Power BI — all from a single storage location.

In this part you will create a Lakehouse, populate it with built-in sample data, and run a SQL query against the resulting Delta table.

---

## Step 1 — Create a Lakehouse

1. In your Fabric workspace, select **+ New item** (or **Create** in the left sidebar) and search for **Lakehouse**.
2. Enter `QuickstartLakehouse` as the name.
3. Keep **Lakehouse schemas (Public Preview)** option **enabled**, then click **Create**.
4. After a few seconds the Lakehouse editor opens with the **Lakehouse explorer** on the left, showing two root folders: **Tables** and **Files**.

   - **Tables** holds managed Delta tables that you can query with SQL.
   - **Files** holds raw files in OneLake (Parquet, CSV, JSON, …) that aren't yet promoted to a table.

![New Fabric Lakehouse editor](/assets/img/workshops/fabric-quickstart/02-new-lakehouse.png)

---

## Step 2 — Load Built-in Sample Data

Fabric ships with curated sample datasets so you can explore the Lakehouse without preparing your own data.

1. In the empty Lakehouse, locate the **Get data in your lakehouse** panel in the center of the editor (it appears automatically when the Lakehouse has no tables yet).
2. Click the **Start with sample data** card. ![Get data in your lakehouse dialog](/assets/img/workshops/fabric-quickstart/02-get-data-dialog.png)
3. From the list of available samples, choose **Public holidays**, then confirm.
4. Fabric runs a short job to copy the dataset into your Lakehouse. Wait for it to complete (typically under a minute). When it finishes, a new `publicholidays` table appears under **Tables**.

![Get data in your lakehouse dialog](/assets/img/workshops/fabric-quickstart/02-get-data-dialog.png)

---

## Step 3 — Explore the Table

1. In the **Lakehouse explorer**, click the `publicholidays` table.
2. The preview pane shows the column schema (`countryOrRegion`, `holidayName`, `date`, `isPaidTimeOff`, …) and the first rows of data.
3. Scroll through the rows to get a feel for the dataset. Because the table is stored as Delta, it is immediately queryable from SQL, Spark, and Power BI with no extra conversion step.

![publicholidays table preview](/assets/img/workshops/fabric-quickstart/02-table-preview.png)

---

## Step 4 — Query the Table with SQL

When you create a Lakehouse, a **SQL analytics endpoint** is automatically provisioned. It exposes your Delta tables to standard `SELECT` statements.

1. In the top-right corner of the Lakehouse, switch the view selector from **Lakehouse** to **SQL analytics endpoint**.
2. Wait for the SQL editor to open, then click **New SQL query**.
3. Paste the following query and click **▷ Run**:

   ```sql
   SELECT TOP 10 countryOrRegion, COUNT(*) AS HolidayCount
   FROM publicholidays
   GROUP BY countryOrRegion
   ORDER BY HolidayCount DESC;
   ```

4. The results pane shows the ten countries or regions with the most recorded public holidays.

![SQL analytics endpoint query result](/assets/img/workshops/fabric-quickstart/02-sql-query.png)

---

## Summary

You now have a Fabric Lakehouse populated with sample data and a working SQL analytics endpoint. In the next part you will connect Power BI in **DirectLake** mode to build a live report over this table — no data movement required.

**Next:** [Part 3 — Upload CSV Data into Lakehouse](/workshops/fabric-quickstart/03-upload-csv/)

---

*Adapted from the Microsoft Learn lab [Create a Microsoft Fabric Lakehouse](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/01-lakehouse.html) ([MIT License](https://github.com/MicrosoftLearning/mslearn-fabric/blob/main/LICENSE)).*
