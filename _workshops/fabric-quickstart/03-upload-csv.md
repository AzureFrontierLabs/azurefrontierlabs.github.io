---
title: "Fabric Quickstart — Part 3: Upload CSV Data into Lakehouse"
description: Download a sample CSV file and upload it into a Fabric Lakehouse, then promote it to a queryable Delta table using Load to Tables.
image:
  path: /assets/img/workshops/fabric-quickstart.png
  alt: Fabric Quickstart Workshop
---

## Overview

In this part you will learn how to upload local files into Lakehouse. You will convert CSV file into a managed **Delta table** — the format that enables SQL, Spark, and PowerBI DirectLake access.

---

## Step 1 — Download the Sample CSV

Before uploading, download the sample sales dataset to your local machine.

1. Click the link below to download the file and save it locally as **sales.csv**:

   **[⬇ Download sales.csv](/assets/data/sales.csv){: download="sales.csv"}**

---

## Step 2 — Upload the File to Lakehouse Files

1. In your Fabric workspace, open `QuickstartLakehouse`.
2. In the **Lakehouse explorer** top menu, locate the **Get data** then click **Upload files**.
3. Click the **folder icon** 📁 to browse files locally and locate the previously saved `sales.csv`, then click **Upload**.
4. Once upload complete click on **Files** in the Lakehouse explorer. The file appears in **Files / sales.csv**.

![Lakehouse Files/data folder showing uploaded sales.csv](/assets/img/workshops/fabric-quickstart/03-upload-files.png)

---

## Step 3 — Load the CSV into a Delta Table

Files in the **Files** section are raw — they can't be queried with SQL yet. Use **Load to Tables** to convert the CSV into a managed Delta table.

1. Click the **…** menu next to **sales.csv**.
2. Select **Load to Tables** → **New table**.
3. In the **Load to table** dialog:
   - **Table name:** `sales`
   - **File type:** CSV
4. Click **Load** to confirm.
5. Fabric runs a Spark job to convert the CSV into a Delta table. The job typically takes 30–60 seconds.

> **Tip:** If the `sales` table doesn't appear automatically when the job finishes, click the **…** menu on the **Tables** folder and select **Refresh**.

![Load to table dialog with table name sales and CSV file type](/assets/img/workshops/fabric-quickstart/03-load-to-table.png)

---

## Step 4 — Preview the Table and Explore the Delta Format

1. In the **Lakehouse explorer**, expand **Tables** and click the **sales** table.
2. The preview pane shows the column schema and first rows of data — `SalesOrderNumber`, `SalesOrderLineNumber`, `OrderDate`, `CustomerName`, `Item`, `Quantity`, `UnitPrice`, `TaxAmount`.

![sales table preview showing schema and first rows](/assets/img/workshops/fabric-quickstart/03-sales-table-preview.png)

3. To see the underlying physical storage, click the **…** menu next to the **sales** table and select **View files**.
4. The **Files** explorer switches to the table's storage path. You will see:
   - One or more **`.parquet`** files — the actual columnar data files.
   - A **`_delta_log/`** subfolder — the Delta transaction log that tracks every change to the table.

> **Why this matters:** Because Fabric stores the table as open Delta format (not a proprietary binary), the same files can be read directly by Apache Spark notebooks, SQL analytics endpoint, and Power BI DirectLake — all without copying or transforming data.

![Delta table files view showing Parquet files and _delta_log folder](/assets/img/workshops/fabric-quickstart/03-delta-table-files.png)

---

## Summary

You have uploaded a CSV file into your Lakehouse and promoted it to a Delta table. In the next part you will connect Power BI using **DirectLake** mode to build a live report directly over this data — no import or scheduled refresh required.

**Next:** [Part 4 — Visualize Lakehouse Data with PowerBI DirectLake](/workshops/fabric-quickstart/04-powerbi-directlake/)

---

*Adapted from the Microsoft Learn lab [Create a Microsoft Fabric Lakehouse](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/01-lakehouse.html) ([MIT License](https://github.com/MicrosoftLearning/mslearn-fabric/blob/main/LICENSE)).*
