---
uid: Connector_help_Skyline_Table_Checker
---

# Skyline Table Checker

This connector will search through the elements with the corresponding protocol on the DataMiner System and look for entries in the desired table based on the configuration parameters set by the user.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

### General

The **General** page includes several key parameters:

- **Update Interval** - Determines how often table checks are performed. The default interval is *30 minutes*.
- **Execute Checks Now** - Button to trigger immediate check instead of waiting for the update interval.
- **Table Checker Last Update** - Displays the timestamp of the most recent table check.
- **Check Results** -  A table that provides details on the checked entries, including the element and protocol name, table and column ID, whether the entry was found, and the number of instances found. These entries are configured in the *Configuration of Checks* table on the **Configuration** Page.

### Configuration

The **Configuration** page allows users to define and manage the table checks by specifying key parameters for each test.

**Configuration of Checks** table contains the following columns:

- *Test Name* – The name of the check.
- *Protocol Name* – The protocol name which acts as a filter to filter only the elements using it.
- *Optional Element Name Regex Filter* – A regular expression filter to refine the element name search.
- *Table PID* – The unique identifier for the table being checked.
- *Column ID* – The specific column within the table being checked.
- *Text to Search On* – The text pattern used to find matches within the column.

The **Update Result Table** button refreshes the results based on the defined checks.