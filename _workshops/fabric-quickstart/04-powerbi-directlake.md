---
title: "Fabric Quickstart — Part 4: Visualize Lakehouse Data with PowerBI DirectLake"
description: Create a DirectLake semantic model over your Fabric Lakehouse tables and build a live PowerBI report without importing or caching data.
image:
  path: /assets/img/workshops/fabric-quickstart.png
  alt: Fabric Quickstart Workshop
---

## Overview

**DirectLake** is a PowerBI storage mode unique to Microsoft Fabric. Instead of importing data into PowerBI or running live SQL queries, DirectLake reads Delta table parquet files directly from OneLake — delivering import-speed performance on always-fresh data.

In this final part you will create a DirectLake semantic model and build a report on top of it.

---

## Step 1 — Create a DirectLake Semantic Model

1. In your Fabric workspace, navigate to your `QuickstartLakehouse`.
2. Click the **New semantic model** button in the top toolbar.
3. Enter `Sales Model` as the name.
4. In the table selection panel, check the **sales** table and click **Confirm**.

Fabric creates a semantic model pre-wired to your Lakehouse via DirectLake — no connection strings or credentials needed.

![New semantic model dialog with sales table selected](/assets/img/workshops/fabric-quickstart/03-semantic-model-create.png)

---

## Step 2 — Add a Measure

Add a simple measure to use in the report:

1. In the semantic model editor, select the **sales** table in the left pane.
2. Click **New measure** in the ribbon.
3. Enter the following DAX expression:

   ```dax
   Total Revenue = SUM(sales[revenue])
   ```

4. Press **Enter** to save. The measure appears under the **sales** table.

![Semantic model editor showing Total Revenue measure](/assets/img/workshops/fabric-quickstart/03-measure.png)

---

## Step 3 — Create a PowerBI Report

1. From the semantic model editor, click **Create report** → **Auto-create report**.
2. Fabric auto-generates a report with visuals based on the data shape. Review the generated report.
3. To customise, switch to **Edit** mode and add a new page:
   - Insert a **Clustered bar chart**: Axis = `product_category`, Values = `Total Revenue`
   - Insert a **Line chart**: X-axis = `order_date` (Month), Values = `Total Revenue`
   - Insert a **Card** visual: Field = `Total Revenue`

![PowerBI report canvas with three visuals](/assets/img/workshops/fabric-quickstart/03-report-canvas.png)

---

## Step 4 — Verify DirectLake Mode

Confirm your report is running in DirectLake (not Import or DirectQuery):

1. In the report, click **Transform data** → **Data source settings**.
2. The connection should show **Microsoft Fabric (DirectLake)** with no import schedule.

> **Why it matters:** DirectLake means your report always reflects the latest data in OneLake without a refresh job. When new data lands in the Lakehouse, reports update automatically.

---

## Step 5 — Publish and Share

1. Click **Save** and name the report `Sales Overview`.
2. The report is saved directly to your Fabric workspace — no separate PowerBI Service publish step is needed.
3. Click **Share** → copy the link to share the report with other workspace members.

![Fabric workspace showing published Sales Overview report](/assets/img/workshops/fabric-quickstart/03-published-report.png)

---

## Summary

You have completed the Fabric Quickstart workshop. Here is what you built:

| Step | What You Did                                                                |
| ---- | --------------------------------------------------------------------------- |
| 1    | Created a Lakehouse, uploaded sample data, and loaded it into a Delta table |
| 2    | Built a DirectLake semantic model and a live PowerBI report                 |

> **Lab cleanup:** If you are running this workshop on the **Azure Frontier Labs** managed platform, your Fabric environment will be automatically deprovisioned when the session timer expires — no manual cleanup is needed.
>
> If you are running this workshop **outside** the managed platform (for example, using your own Fabric trial or subscription), delete the workspace when you are done to avoid ongoing charges: open the workspace, go to **Workspace settings** → **General** → **Remove this workspace**.
