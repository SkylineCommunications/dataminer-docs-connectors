---
uid: Connector_help_Skyline_Masking_Services
---

# Skyline Masking Services

This virtual connector reads and parses USAGM-specific Excel files representing a bookings program schedule. In conjunction with a Correlation rule, Automation script, services, and Visio files, this allows you to suppress alarms on a service or program level.

## About

### Key Features

- **Parsing proprietary Excel sheets into a scheduling table**: This connector is able to parse and display booking schedules as well as determine which bookings are active, all based on an Excel file.
- **Multiple bookings schedules**: This connector has the capability of parsing multiple bookings schedules at once.
- **Service Tracking**: This connector displays every service available on the DMA in a table.
- **Row config**: Should the order of columns in the Excel file change, you can update the row location of the various parameters.

## Use Case

- **Challenge**: Hundreds of inactive programs may still display alarms that are not important, making it difficult to focus on the alarms that do require attention.
- **Solution**: This connector, in conjunction with an interactive Automation script, will mask all inactive programs and unmask when they become active.
- **Benefit**: You no longer need to deal with an overload of "false positive" alarms but are able to focus on the things that truly need your attention.

## Technical info

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Skyline Masking Services, refer to the [Technical help page](xref:Connector_help_Skyline_Masking_Services_Technical).
