---
title: "Fabric Quickstart — Part 1: Claim Your Fabric Environment"
description: 
---

## Welcome to the Fabric Quickstart

In this workshop you will build an end-to-end analytics solution on **Microsoft Fabric** — from ingesting raw data into a Lakehouse all the way to live PowerBI reports powered by DirectLake.

This first part walks you through claiming your isolated lab environment so you are ready to start building.

### Prerequisites

- An active Azure Frontier Labs account
- A web browser (Chrome or Edge recommended)

### Workshop Structure

| Part | Topic                                            |
| ---- | ------------------------------------------------ |
| 1    | Claim Your Fabric Environment (this page)        |
| 2    | Getting Started with Fabric Lakehouse            |
| 3    | Upload CSV Data into Lakehouse                   |
| 4    | Visualize Lakehouse Data with PowerBI DirectLake |

---

## Step 1 — Log in to the Azure Frontier Labs Portal

Navigate to [azurefrontierlabs.com/join](https://azurefrontierlabs.com/join) and paste the **lab code** and your **work email** address and click **Next**.

![Azure Frontier Labs — signin](/assets/img/workshops/fabric-quickstart/01-labs-dashboard.png)

Review and accept terms and conditions and click **Join Lab**.

![Azure Frontier Labs dashboard — accept TOS](/assets/img/workshops/fabric-quickstart/01-terms.png)

You received a temporary environment **username** and **password** to access your dedicated Microsoft Fabric environment. In the next steps you will sign-in into Microsoft Fabric using these credentials. Click on [**Open Microsoft Fabric**](https://app.fabric.microsoft.com/).

![Azure Frontier Labs dashboard — obtain credentials](/assets/img/workshops/fabric-quickstart/01-obtain-credentials.png)

Fill temporary username you've obtained and click **Submit**. On the next screen fill the password you've got from the claim lab.

![Azure Frontier Labs dashboard — fill user name](/assets/img/workshops/fabric-quickstart/01-login-to-fabric-username.png)

## Step 2 — Complete MFA setup

In the next screen you will need to complete MFA setup, this is required to use this environment.

Click **Next**

![MFA setup — initial prompt, click Next](/assets/img/workshops/fabric-quickstart/01-mfa1.png)

Download Microsoft Authenticator app to your phone and click **Next**.

![MFA setup — download Microsoft Authenticator prompt](/assets/img/workshops/fabric-quickstart/01-mfa2.png)

Click **Next**.

![MFA setup — add account in Authenticator, click Next](/assets/img/workshops/fabric-quickstart/01-mfa3.png)

Use  Microsoft Authenticator App to scan the QR code. Then click **Next**.

![MFA setup — QR code to scan with Authenticator app](/assets/img/workshops/fabric-quickstart/01-mfa4.png)

On your phone fill the number shown on screen.

![MFA setup — enter the number shown on screen into Authenticator](/assets/img/workshops/fabric-quickstart/01-mfa5.png)

Complete MFA setup by clicking on **Done**.

![MFA setup — confirmation screen, click Done](/assets/img/workshops/fabric-quickstart/01-mfa6.png)

---

## Step 3 — Launch the Fabric Workspace

Click on **Workspaces** on the left sidebar and then click on the workspace with the lab name. The workspace name is generated dynamically when this lab was created. It's name starts with **ws-{lab name}-{claim number}**. For example **ws-lab-ede4-001**. This is your workspace for the entire LAB. All the Fabric items must be created inside this workspace to work correctly.

![Fabric workspace home screen](/assets/img/workshops/fabric-quickstart/01-fabric-workspace.png)

---

## Summary

You now have a running Microsoft Fabric environment and a dedicated workspace. In the next part, you will create a Lakehouse and load data into it.

**Next:** [Part 2 — Getting Started with Fabric Lakehouse](/workshops/fabric-quickstart/02-fabric-lakehouse/)
