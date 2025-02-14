---
uid: Connector_help_Skyline_Masking_Services_Technical
---

# Skyline Masking Services

## About

This virtual connector reads and parses USAGM-specific Excel files representing a bookings program schedule. In conjunction with a Correlation rule, Automation script, services, and Visio files, this allows you to suppress alarms on a service or program level.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you have created the element, the following configuration is required in order to initialize it:

1. Set the **Excel Import Path** parameter to the path containing the Excel documents to be parsed. If you specify a directory containing multiple Excel files, all of these files will be parsed at once.

1. Check the **Row Config** against the Excel file for formatting changes. Generally, there will be no such changes, but if parsing went wrong, you will have to update the various Rows/Program Start/UTC Column parameters to match the Excel file.

1. Click the **Refresh** Button.

   Excel files will now be parsed and tables will be filled in. Check the **Import Status Message** parameter for any errors that may occur during parsing.

## Usage

The following data pages are available in an element created with this connector:

- **General**: Contains various parameters such as the *Config* parameters and the *Row config* parameters. The latter define where in the Excel file various parameters will be found.
- **Schedules**: Contains a table with the full schedule of program data.
- **Filtered Programs**: Contains a table with the full list of programs.
- **Active Programs**: Contains a table with the list of active programs only.
- **Services**: Contains a table with every existing service on the DMA.
- **Audit Trail**: Lists audit trail information.
