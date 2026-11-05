---
uid: Connector_help_Skyline_Table_Checker_Technical
---

# Skyline Table Checker

## About

With this connector, you can search through all the elements in your DataMiner System that use a specific connector (also known as "protocol") and look for specific entries in a table of your choice.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

### General Page

The **General** page includes several key parameters:

- **Update Interval**: Determines how often table checks are performed. The default interval is *30 minutes*.
- **Execute Checks Now**: Allows you to trigger an immediate check instead of waiting for the update interval.
- **Table Checker Last Update**: Displays the timestamp of the most recent table check.
- **Check Results**: Provides details on the checked entries, including the element and protocol name, table and column ID, whether the entry was found, and the number of instances found. These entries are configured in the **Configuration of Checks** table on the **Configuration** page.

### Configuration Page

The **Configuration** page allows you to define and manage the table checks by specifying key parameters for each test.

The **Configuration of Checks** table contains the following information:

- **Test Name**: The name of the check.
- **Protocol Name**: The protocol name that is used as a filter. Only the elements using this protocol will be checked.
- **Optional Element Name Regex Filter**: A regular expression filter to refine the element name search.
- **Table PID**: The unique identifier for the table being checked.
- **Column ID**: The specific column within the table being checked.
- **Text to Search On**: The text pattern used to find matches within the column.

The **Update Result Table** button refreshes the results based on the defined checks.
