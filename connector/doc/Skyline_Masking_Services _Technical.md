---
uid: Connector_help_Skyline_Masking_Services_Technical
---

# Skyline Masking Services

This virtual connector reads and parses USAGM-specific Excel files representing a bookings program schedule. In conjunction with a correlation rule, automation script, services, and Visio files the user is able to suppress alarms on a service or program level.

## About

### Version Info

| Range   | Key Features     | Based on | System Impact |
|---------|------------------|----------|---------------|
| 1.0.0.x | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -              |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### General

Contains various parameters such as the *Config* parameters, and the *Row config* parameters which define where in the excel various parameters will be found.

### Schedules

Contains the Schedules table - the full schedule of program data.

### Filtered Programs

Contains the *Programs* table - full list of programs.

### Active Programs

Contains the *Active Programs* table - list of only active programs.

### Services

Contains the Services table - every existing service in the DMA

### Audit Trail

Contains the *Audit Trail* table.

## Requirements
On startup of the element, user must do the following

-Set the Excel Import Path parameter to the path containing the Excel documents to be parsed. *Note: Directories containing multiple Excel files will result in parsing of all at once*
-Check the Row Config against the Excel file for formatting changes: Generally these will not change, but if parsing is wrong, will have to update the various Rows/Program Start/UTC Column parameters to match that of the Excel files.
-Click the Refresh Button - Excel files will now be parsed/tables will be filled. Consult the *Import Status Message* parameter for any errors that may occur during parsing.
