---
uid: Connector_help_Skyline_Masking_Services
---

# Skyline Masking Services

This virtual connector reads and parses USAGM-specific Excel files representing a bookings program schedule. In conjunction with a correlation rule, automation script, services, and Visio files the user is able to suppress alarms on a service or program level.

## About

### Key Features

- **Parsing Proprietary Excel Sheets into Scheduling Table**: This driver is able to parse and display booking schedules as well as determine which bookings are active, all from the Excel.
- **Multiple Bookings Schedules**: This connector has the capability of parsing multiple bookings schedules at once.
- **Service Tracking**: This connector displays every service available on the DMA in a table.
-**Row config***: Should the order of columns in the excel change, the user can update the row location of various parameters on the **General** Page.

## Use Cases

### Writing this marketing document

**Challenge:** 
User has hundreds of inactive programs which are still displaying alarms that are not important.
**Solution:** 
This driver, in conjunction with an Interactive Automation Script, will mask these inactive programs and unmask when they become active.
**Benefit:** 
User is not flooded with "false positive" alarms.

## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Skyline Masking Service connector.

[!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Skyline Masking Services, refer to the [Technical help page](xref:Connector_help_Skyline_Masking_Services_Technical).
