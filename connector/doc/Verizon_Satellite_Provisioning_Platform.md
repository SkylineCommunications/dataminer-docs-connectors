---
uid: Connector_help_Verizon_Satellite_Provisioning_Platform
---

# Verizon Satellite Provisioning Platform

## About

This connector integrates DataMiner with the Verizon Satellite Provisioning Platform and maintains a local **VSAT database**. It retrieves and keeps provisioning data synchronized for **circuits, locations, location equipments, devices, customers, outage contacts, contact infos, and ESP PIRs**.

The **General** page provides a high-level overview with total item counts per dataset, allowing quick validation of whether the data is up to date.

## Key Features

- **Automated data synchronization**: Keep all Verizon provisioning datasets (e.g. circuits, locations, devices, customers) continuously in sync, ensuring decisions are based on the latest information.

- **Granular polling control**: Configure per-dataset polling intervals, enable/disable datasets, and trigger on-demand polling to refresh exactly what you need, when you need it.

- **Actionable status and progress visibility**: Validate data freshness at a glance via total item counts and per-dataset status, reason, and page processing indicators to quickly spot and resolve issues.

- **Reliable file export workflow**: Automatically export consolidated datasets to a defined path after polling completes, with a manual export option and clear export status/timestamps for auditability.

- **Secure, guided authentication**: Simple login flow with immediate success feedback, reducing setup friction and ensuring the connector only runs when credentials are valid.

## Configuration

### HTTP Connection

When you create a DataMiner element using this connector in DataMiner Cube, you will need to specify the following details for the HTTP connection:

- **IP address/host**:
  - Production: `https://satellite-provisioning.verizon.com`
  - UAT: `https://satellite-provisioning.verizon-uat.com`
- **IP port**: `443`

### Authentication

Once the element has been created, you will need to set up the authentication before data can be retrieved:

1. Open the **Configuration** page.
1. Under **Authentication**, enter the **API Username** and **API Password**.
1. Click **Login**.
1. Verify that **Login Status** shows **Success** before enabling polling.

### Polling Settings

1. Open the **Polling Settings** page.
1. Each row represents a dataset (Circuits, Customers, Locations, Devices, Contact Info, Outage Contacts, Location Equipments, ESP PIRs).
1. Configure the following:
   - **State**: Enable or disable polling for the dataset.
   - **Interval**: Determines how often the dataset is refreshed (default: once per day).
   - **Items Per Page**: Controls how many items are requested per page in the API responses. Default value: 250.
   - **Poll**: Triggers immediate polling for the selected dataset.
1. Use **Status** and **Reason** to confirm that all pages have been processed successfully.

### File Export

1. Go to the **Configuration** page.
1. In **Export Configuration**:
   - Enable **File Export**.
   - Set the **File Export Path** where files should be written.

Once this has been configured, the export will run **automatically after the Polling Manager finishes processing all enabled datasets**.

To manually trigger an export at any time, you can use the **Export Now** option.

Check the **File Export Status** and **Last Exported** parameters to confirm whether an export has been successfully completed.

## Daily Operation

When the element has been fully configured as detailed above:

- The connector runs autonomously.
- Data is refreshed based on the polling intervals.
- File exports are generated automatically once polling completes.
- Users can browse the data through the Circuits, Locations, Devices, and related pages.
