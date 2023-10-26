---
uid: Telenor_Customer_Validation_Mediator
---

# Telenor Customer Validation Manager

This protocol reads a CSV File and stores it in a table that can be used as a data source in for example a GQI Query.

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

You do not need to do anything to initiate the connector. However, to use the connector by filling the table, you need to specify a path to a matching CSV file in the parameter **Path to Mapping CSV**. 

## How to use

Note that the CSV file needs to contain at least two columns, one with the header "Household ID" and one with the header "Device ID". The expected separator is a *,*. 

With the toggle button **Filter Only on STBs**, you can specify if you want to filter out not-STB's or not. STB is in this context the abbreviation for Set Top Box. 

By clicking the button **Parse CSV to Table**, you can trigger a parse operation of the CSV File to the table. This table will lose the previous content. 
