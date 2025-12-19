---
uid: Connector_help_Verizon_Satellite_Provisioning_Platform
---

# Verizon Satellite Provisioning Platform

## Overview
This connector integrates DataMiner with the Verizon Satellite Provisioning Platform and maintains a local **VSAT database**.  
It retrieves and keeps provisioning data synchronized for **circuits, locations, location equipments, devices, customers, outage contacts, contact infos, and ESP PIRs**.

The **General** page provides a high-level overview with total item counts per dataset, allowing quick validation that the data is up to date.

---

## Key Features

- **Automated Data Synchronization**  
  Keep all Verizon provisioning datasets (e.g., circuits, locations, devices, customers) continuously in sync, ensuring decisions are based on the latest information.

- **Granular Polling Control**  
  Configure per-dataset polling intervals, enable/disable datasets, and trigger on-demand polls to refresh exactly what you need, when you need it.

- **Actionable Status & Progress Visibility**  
  Validate data freshness at a glance via total item counts and per-dataset status, reason, and page processing indicators to quickly spot and resolve issues.

- **Reliable File Export Workflow**  
  Automatically export consolidated datasets to a defined path after polling completes, with manual “Export Now” and clear export status/timestamps for auditability.

- **Secure, Guided Authentication**  
  Simple login flow with immediate success feedback, reducing setup friction and ensuring the connector only runs when credentials are valid.

---

## How to Use

### Creation

#### HTTP Main Connection
This connector uses an HTTP connection and requires the following input during element creation:

**HTTP Connection**
- **IP address / host**  
  - Production: `https://satellite-provisioning.verizon.com`  
  - UAT: `https://satellite-provisioning.verizon-uat.com`
- **IP port**: `443`

---

### Configure Authentication
1. Open the **Configuration** page.
2. Under **Authentication**, enter the **API Username** and **API Password**.
3. Click **Login**.
4. Verify that **Login Status** shows **Success** before enabling polling.

---

### Polling Manager (Polling Settings)
1. Open the **Polling Settings** page.
2. Each row represents a dataset (Circuits, Customers, Locations, Devices, Contact Info, Outage Contacts, Location Equipments, ESP PIRs).
3. Configure the following:
   - **State**: Enable or disable polling for the dataset.
   - **Interval**: How often the dataset is refreshed (default: once per day).
   - **Items Per Page**:  
     Controls how many items are requested per page in the API responses.  
     Default value is **250**.
   - **Poll**: Triggers an immediate poll for the selected dataset.
4. Use **Status** and **Reason** to confirm that all pages were processed successfully.

---

### File Export
1. Go to the **Configuration** page.
2. In **Export Configuration**:
   - Enable **File Export**.
   - Set the **File Export Path** where files should be written.
3. The export runs **automatically after the Polling Manager finishes processing all enabled datasets**.
4. Use **Export Now** to manually trigger an export at any time.
5. Check **File Export Status** and **Last Exported** to confirm completion.

---

## Daily Operation
After authentication, polling, and export are configured:
- The connector runs autonomously.
- Data is refreshed based on the polling intervals.
- File exports are generated automatically once polling completes.
- Users can browse the data through the Circuits, Locations, Devices, and related pages.
