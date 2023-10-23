---
uid: Connector_help_Telenor_Customer_Validation_Manager
---

# Telenor Customer Validation Manager

This connector serves the essential function of conducting a 30-day validation period, ensuring a high level of quality and stability in the television service provided to new Fixed Wireless Access (FWA) customers. 
During this validation period, a comprehensive analysis of key performance indicators (KPIs) and reported error events is performed, resulting in updated status reports for each household or device every 24 hours.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version  | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | \-                     |

### System Info

| **Range** | **DCF Integration** | **Cassandra Compliant** | **Linked Components**                                                                                                                                                                                                                                                                                                  | **Exported Components** |
|-----------|---------------------|-------------------------|---------------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     |  \-                       | \-                      |


## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

In order to execute a straightforward validation process, the user must furnish the appropriate username and password, granting access to the necessary folders: LPI folder, SDP folder, DataSources folder, and DataAggregator folder. 
Customization of these settings can be accomplished through the Configuration and Credentials page.

Additionally, users are required to fine-tune the thresholds for Key Performance Indicators (KPIs) and error codes to ensure precise validation. 
To add new error codes to the system, users can conveniently employ the Context menu by right-clicking within the "Error Codes" table.

Users are also afforded the flexibility to configure the retention period of validation records in the table (default 30 days) and set the maximum offset for initiating a new validation. 
A monitoring service is available as well. When a specific service remains in a critical state beyond the specified threshold, the validation for that particular day will be disregarded.

## How to Use

### General

On this page, users have the option to manually initiate a new validation by simply clicking the "Start" button. 
The household table displays a comprehensive list of eligible households ready to initiate a fresh validation (or already in validation).

Subsequently, the outcomes and findings will be accessible through the Validation and Error Events pages for the user's convenience.

### Statistics

On this page, the user can see statistical data for the specied validation period. There is also a button that allows the user to reset all counters.
