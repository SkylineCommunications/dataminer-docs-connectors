---
uid: Connector_help_Telenor_Customer_Validation_Mediator
---

# Telenor Customer Validation Mediator

This connector reads a CSV file and stores it in a table that can be used as a data source in for example a GQI query.

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                     |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

You do not need to do anything to initiate the connector. However, to fill in the table based on a CSV file, you will need to specify the CSV file as detailed below.

## How to use

To fill in the table based on a CSV file, you need to specify a path to the CSV file in the parameter **Path to Mapping CSV**.

The CSV file needs to contain at least two columns, one with the header "Household ID" and one with the header "Device ID". The expected separator is a comma (",").

By clicking **Parse CSV to Table**, you can trigger a parse operation of the CSV file to the table. This table will lose its previous content.

With the toggle button **Filter Only on STBs**, you can specify if you want to filter out non-STBs or not. STB in this context is the abbreviation for Set-Top Box.
