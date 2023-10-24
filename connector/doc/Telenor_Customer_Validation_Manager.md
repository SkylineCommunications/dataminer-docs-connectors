---
uid: Connector_help_Telenor_Customer_Validation_Manager
---

# Telenor Customer Validation Manager

This connector serves the essential function of conducting a 30-day validation period, ensuring a high level of quality and stability in the television service provided to new Fixed Wireless Access (FWA) customers. During this validation period, a comprehensive analysis of key performance indicators (KPIs) and reported error events is performed, resulting in updated status reports for each household or device every 24 hours.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **Configuration** and **Credentials** page of the element, you need to specify the appropriate username and password to make sure the connector can access the LPI folder, SDP folder, DataSources folder, and DataAggregator folder. This is necessary to be able to execute the validation process.

You also need to fine-tune the thresholds for Key Performance Indicators (KPIs) and error codes to ensure precise validation. To add new error codes to the system, use the right-click menu of the **Error Codes** table.

You can also configure the retention period of validation records in the table (by default 30 days) and set the maximum offset for initiating a new validation.

A monitoring service is available as well. When a specific service remains in a critical state beyond the specified threshold, the validation for that particular day will be disregarded.

## How to Use

On the **General** page, you can manually initiate a new validation by clicking the **Start** button. The household table displays a comprehensive list of households where a new validation can be initiated or where validation is already ongoing.

The outcome and findings of the validation are available on the **Validation** and **Error Events** pages.

The **Statistics** page displays statistical data for the specified validation period. There is also a button that allows you to reset all counters.
